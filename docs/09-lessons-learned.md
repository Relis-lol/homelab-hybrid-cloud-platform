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
* Added additional market-quality metrics

**Result**

* More realistic profit estimates
* Better trade recommendations

---

## 🧩 Monolithic Components Become Difficult To Maintain

**Problem**

* API and worker layers accumulated unrelated responsibilities
* Debugging became increasingly difficult

**Solution**

* Split large files into dedicated modules
* Separated:

  * API features
  * ingestion
  * enrichment
  * orchestration
  * reporting

**Result**

* Improved maintainability
* Easier troubleshooting
* Faster feature development

---

## 📈 Data Quality Matters More Than Visualization

**Problem**

* Missing or inconsistent data produced misleading charts

**Solution**

* Improved validation and preprocessing
* Added better handling for incomplete datasets

**Result**

* More reliable analytics
* Better dashboard experience

---

## 🎯 Key Takeaway

The largest improvements came from architecture, data quality, and operational reliability rather than adding new features.

Investing in maintainable systems consistently produced better results than increasing feature count.
