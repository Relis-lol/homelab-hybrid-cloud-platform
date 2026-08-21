# 🛠️ Lessons Learned

Selected technical challenges encountered during development and the architectural decisions that followed.

---

## 🚨 Full Market Imports Do Not Scale

**Problem**

* Large regional imports caused unstable execution
* ESI timeouts became increasingly common

**Solution**

* Introduced incremental page-based synchronization
* Added region-specific page budgets
* Added sync-state tracking

**Result**

* More reliable imports
* Predictable runtime behavior
* Lower API load

---

## 🏪 Regions Are Not Trade Hubs

**Problem**

* Full-region market data produced misleading trade opportunities
* Non-hub stations distorted pricing

**Solution**

* Added explicit trade-hub filtering
* Limited core analytics to:

  * Jita
  * Amarr
  * Dodixie
  * Hek
  * Rens

**Result**

* More realistic trading calculations
* Better arbitrage analysis
* Cleaner logistics data

---

## 📦 Bulk Imports Beat Item-By-Item Lookups

**Problem**

* Missing items were imported individually
* Synchronization became unnecessarily slow

**Solution**

* Switched to bulk page imports
* Filtered data locally

**Result**

* Faster enrichment runs
* Fewer API requests
* Simpler synchronization logic

---

## 💸 Raw Profit Is Not Real Profit

**Problem**

* Simple price spreads overstated profitability
* Trading fees were ignored

**Solution**

* Introduced fee-aware calculations
* Added market-quality metrics
* Integrated liquidity-aware evaluation

**Result**

* More realistic profit estimates
* Better trade recommendations
* Fewer misleading opportunities

---

## 🧩 Monolithic Components Become Difficult To Maintain

**Problem**

* API and worker layers accumulated unrelated responsibilities
* Large files became difficult to navigate and debug

**Solution**

* Split the API into dedicated feature modules

* Split the worker into:

  * ingestion
  * enrichment
  * orchestration
  * reporting
  * analytics

* Reduced monolithic files into focused components

**Result**

* Improved maintainability
* Easier troubleshooting
* Faster feature development
* Cleaner architecture

---

## 📈 Data Quality Matters More Than Visualization

**Problem**

* Missing or inconsistent data produced misleading charts
* Frontend improvements could not compensate for poor data quality

**Solution**

* Improved validation and preprocessing
* Added better handling for incomplete datasets
* Tightened analytics filtering

**Result**

* More reliable analytics
* Better dashboard experience
* Increased confidence in recommendations

---

## 🧮 Data Types Can Break Business Logic

**Problem**

* SQL calculations returned decimal values where integer quantities were expected
* Cargo volume calculations became distorted
* Trade Looper recommendations showed unrealistic hauling volumes

**Solution**

* Reviewed numeric handling in SQL result processing
* Separated quantity logic from price and volume calculations
* Tightened conversion rules between database results and API responses

**Result**

* More realistic cargo metrics
* Cleaner trade recommendation output
* Better confidence in logistics calculations

---

## 🔄 Monitoring Matters Before Failure

**Problem**

* Worker failures were not immediately visible
* Infrastructure health required manual checks
* Operational issues could remain unnoticed

**Solution**

* Added Discord alerting
* Integrated Azure Monitor and Azure Arc
* Implemented a dedicated ESP32 CYD monitoring display
* Added structured execution tracking

**Result**

* Faster issue detection
* Better operational visibility
* Reduced manual monitoring effort
* Improved platform reliability

---

## 🌐 Internal Health Does Not Guarantee Public Availability

**Problem**

* Multiple production incidents occurred while all internal services appeared healthy
* Docker containers, API, database and workers reported normal operation
* Users could still not reach the public website due to DNS and connectivity issues

**Solution**

* Implemented automated Cloudflare DDNS updates
* Added external website reachability monitoring
* Added Cloudflare DDNS logging and validation
* Integrated Discord alerting for public availability failures
* Added website status visibility to the ESP32 monitoring dashboard
* Removed hard-coded local network dependencies from frontend API communication

**Result**

* Faster root-cause identification
* Improved resilience against ISP IP changes
* Better visibility into real user experience
* Reduced recovery time during connectivity incidents
* Stronger operational reliability

---

## ⏱️ Scheduled Jobs Need Concurrency Control

**Problem**

* A duplicated cron configuration allowed worker jobs to overlap during scheduled execution
* Overlapping workers created duplicate database writes in high-volume market tables
* Over roughly two weeks, the issue produced more than 100 million unnecessary rows
* Database storage usage increased significantly and growth became harder to predict

**Solution**

* Added explicit concurrency control for scheduled worker execution using `flock`
* Reviewed and cleaned the active crontab configuration
* Removed duplicated runtime data from affected database tables
* Added stronger validation around worker scheduling and runtime behavior

**Result**

* Only one worker instance can run at a time
* Overlapping imports are skipped instead of running in parallel
* More than 100 million unnecessary rows were removed
* Database growth became predictable again
* Scheduled background execution is now safer and easier to operate

---

## 🧯 Production Reviews Are Feature Work

**Problem**

* The platform had grown beyond a simple dashboard into a live production system
* Database growth, backups, log volume, worker scheduling and port exposure became operational concerns
* These issues were not visible from feature testing alone

**Solution**

* Performed a post-deployment architecture and operations review using an AI-assisted code audit as one input
* Verified findings independently before applying changes
* Tested fixes in a separate development clone before production rollout
* Focused improvements on reliability, observability, storage management and production safety

**Result**

* High-volume database tables now have retention controls
* Scheduled workers are protected against overlap
* API errors are safer for public clients
* Logs and backups are easier to operate over time
* The project gained a repeatable review-improve-deploy workflow instead of only accumulating new features

---

## 💾 Backups Need To Protect The Backup Target Too

**Problem**

* Backup automation checked only part of the data footprint before writing new dumps
* A growing external backup SSD could reach full capacity while the main services still appeared healthy
* Failed backups created a recovery risk that normal application monitoring would not catch

**Solution**

* Expanded backup storage checks across the relevant data directories
* Added pressure-aware cleanup behavior
* Kept an instant-restore backup copy outside the normal deletion rotation
* Included backup logs in the operational review workflow

**Result**

* Backup failures are easier to detect
* Restore workflows are safer
* Storage pressure is treated as an operational signal, not only a disk-space problem

---

## 🧭 Containers Do Not Cache DNS

**Problem**

* Background import runs began aborting with name-resolution errors
* The failures were not specific to the market API — unrelated external hosts failed in the same moment, which ruled out an upstream API problem
* Frequency grew from a handful per day to around ninety
* Root cause: containers have no DNS cache of their own. Every single lookup is forwarded to the host resolver and from there to the home router, which intermittently stopped answering in time
* The import worker made the load worse by opening a new connection per page, so one regional sync resolved the same hostname over a hundred times

**Solution**

* Added a local caching resolver on the host, with two independent upstream providers instead of the router alone
* Enabled stale-answer serving, so a brief upstream outage returns a slightly outdated record instead of failing
* Pointed the host resolver at it — containers follow automatically, because they already resolve through the host
* Reused a single HTTP session in the worker, so a sync resolves the hostname once instead of once per page

**Result**

* Name-resolution failures stopped completely
* Repeated lookups answer from memory instead of crossing the network
* Connection reuse cut repeat request latency by more than half
* No container restart and no downtime were required

**Follow-up**

* The resolver occasionally failed to start after a reboot, because it starts
  before the container runtime's internal network interface exists and could
  not bind to it yet
* Fixed with an explicit systemd ordering override so the resolver always
  starts after the container runtime is up
* Found and fixed independently, without walking through the earlier
  diagnostic steps again — the ownership of this piece of infrastructure has
  shifted

---

## 🧪 Verify Infrastructure Assumptions Before The Maintenance Window

**Problem**

* The planned fix was to point the container runtime directly at the new resolver, which would have required restarting every service
* A maintenance window had already been scheduled around that assumption
* The assumption looked obvious and had never been tested

**Solution**

* Ran throwaway containers on the production network with the intended settings, without touching any running service
* Both variants failed immediately: an explicitly configured resolver address is interpreted inside the container namespace, and the host bridge address is unreachable across isolated container networks
* The existing setup only worked because a loopback resolver in the host configuration is a special case, served from the host namespace — which cannot be reproduced through explicit configuration
* Chose the indirect path instead: change only the host resolver and let the containers follow

**Result**

* The restart of all services turned out to be unnecessary
* The change landed with zero downtime
* A flawed plan was caught in a five-minute test instead of during a maintenance window

---

## 🕵️ Behind A CDN, The Proxy Sees The CDN

**Problem**

* The reverse proxy was missing its real-IP directives, so every request appeared to come from a CDN edge address
* Access logs were therefore useless for visitor statistics
* More seriously, the API rate limit bucketed requests per CDN edge node instead of per visitor — visitors sharing an edge node silently shared one budget
* Stored sender addresses for contact and wiki submissions pointed at the CDN as well
* Nothing failed visibly, which is why it went unnoticed for months

**Solution**

* Added the CDN networks as trusted sources and switched the proxy to the CDN's client-address header
* Verified afterwards that logged addresses were real client addresses

**Result**

* One change fixed logging, rate limiting and submission records at once
* Rate limiting now applies per visitor as originally intended
* Applied with a configuration reload — no restart, no downtime

---

## 🔎 Content Behind URL Fragments Is Invisible To Search Engines

**Problem**

* The knowledge base held close to 2,000 articles, every one of them reachable
  only through a URL fragment of the form 
* Everything after the  belongs to the same URL as far as search engines are
  concerned, so the entire knowledge base counted as a single page
* The site had no sitemap, no meta description, no canonical and no social
  preview data at all; the crawler had requested a robots.txt twice and
  received a 404 both times
* Nothing about this was visible as a fault. The site worked perfectly for
  anyone who already knew it existed

**Solution**

* Added the basics first, because they cost nothing and one of them was
  actively being asked for: robots.txt, sitemap, meta description, canonical,
  Open Graph data and a generated preview image
* Pre-rendered a pilot set of articles as fully static pages that need no
  JavaScript at all, generated automatically from the same source data
* Introduced a separate public-slug mapping. Internal identifiers ran up to
  108 characters and some carried version fragments, neither of which belongs
  in a permanent canonical URL. Internal identifiers and old shared links were
  left untouched
* Kept the existing genuine 404 handling instead of the common single-page
  fallback that answers every unknown path with the start page. That pattern
  produces soft 404s, which is worse than the problem it solves

**Result**

* Individual guides became addressable, linkable and indexable
* Old shared links still work and now resolve to the new pages, and the
  interactive application was left completely unchanged
* Measured before rollout: full article text present without JavaScript,
  unique metadata per page, all internal targets resolving, unknown paths
  still returning a real 404

**Also learned**

Database-generated pages were checked separately before any of them were
published. Word count alone looked healthy, but all of them shared a single
section structure with text similarity between 0.90 and 1.00. They were kept
out of the sitemap and out of the index pending a separate review of whether
individual categories carry standalone value. Volume is not the same thing as
substance, and measuring that took one query.

---

## 📰 A Feature Can Be Well-Built And Still Not Earn Its Keep

**Problem**

* A news system was built as a genuine production feature: multiple content
  sources, an AI rewriter pass, live killmail signals, translation, and a
  custom WebGL widget as its visual centerpiece
* It ran in production for weeks on its own compute budget, competing for the
  same CPU headroom as the market-data pipeline
* Despite the investment and the lore-driven presentation, it did not
  measurably grow visitor engagement over the tools that were already there

**Solution**

* Paused it deliberately rather than continuing to run it on inertia:
  disabled the AI rewriter and the hourly feed pipeline, hid the news popup
  and its toggle, and stopped the background killmail collector feeding it
* Kept the purely decorative widget it introduced running on its own, since
  it carries no pipeline cost and was never the part competing for resources
* Every piece was disabled rather than deleted, each independently
  reversible, so the decision costs nothing to revisit later

**Result**

* The compute budget the feature was consuming is now available for
  something with a clearer return
* Nothing about the decision is permanent or destructive — turning it back on
  is a configuration change, not a rebuild
* The lesson is the honest read of the data, not the build itself: shipping a
  feature well is necessary but not sufficient, and recognizing that a
  well-executed idea still isn't earning its keep is a separate skill from
  building it in the first place

---

## 🎯 Key Takeaway

The largest improvements came from architecture, data quality, observability, and operational reliability rather than adding new features.

Investing in maintainable systems consistently produced better results than increasing feature count.

A reliable system is not defined by healthy internal services alone. Real reliability means ensuring that users can actually reach and use the platform under real-world conditions, while scheduled background jobs remain controlled, observable, storage-aware, and safe against accidental overlap.
