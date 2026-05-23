# Live Market Dashboard

Interactive browser-based EVE market dashboard connected to a real backend API and historical market database.

The dashboard combines cargo valuation, historical market analysis, and modular frontend tools into a unified interface powered by live EVE Online market data.

---

# Current Features

- Live cargo value calculation
- Historical market charts
- Multi-tab dashboard system
- Dynamic chart tabs
- Trade utility integration
- Responsive dark UI
- Real API-connected data flow
- Clickable item interactions
- Historical price statistics
- Browser-based frontend architecture

---

# Dashboard Structure

Current frontend modules:

- Cargo Value
- Charts
- Trade Calculator
- Route Risk
- WH Mapping

The dashboard uses a shared tab-based interface with modular feature separation.

---

# Cargo Value Workflow

The Cargo Value module supports direct copy/paste input from EVE Online inventory windows.

Example workflow:

```text
CTRL+C from EVE
→ Paste into dashboard
→ API request
→ Live market lookup
→ Total value calculation
→ Interactive item results
