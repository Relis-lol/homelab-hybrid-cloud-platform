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

## 🎯 Key Takeaway

The largest improvements came from architecture, data quality, observability, and operational reliability rather than adding new features.

Investing in maintainable systems consistently produced better results than increasing feature count.
