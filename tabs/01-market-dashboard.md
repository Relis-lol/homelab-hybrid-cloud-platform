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
````

---

# Current Cargo Features

* Multi-item parsing
* Quantity detection
* Invalid line handling
* Missing item detection
* Real market price calculation
* ISK formatting
* Clickable item rows
* Direct chart integration

---

# Historical Chart System

Items inside the Cargo Value results can directly open historical market charts.

### Current Chart Features

* Historical average price tracking
* Adjusted price visualization
* Multiple open chart tabs
* Closable chart tabs
* Automatic focus behavior
* Time range selection
* Basic price statistics

### Statistics

Current chart statistics include:

* Latest price
* Minimum price
* Maximum price
* Percentage change

---

# API Integration

The dashboard is connected to the FastAPI backend and PostgreSQL market database.

### Current Data Flow

```text
Frontend
→ FastAPI
→ PostgreSQL
→ Historical Market Data
→ API Response
→ Interactive UI Rendering
```

### Design Principles

* No direct database access from frontend
* Backend handles calculations and validation
* Frontend focuses on interaction and visualization
* Modular API-driven architecture

---

# UI & Frontend Design

The frontend follows a lightweight EVE-inspired dark UI design.

### Current Focus Areas

* Fast browser rendering
* Responsive layout behavior
* Modular tab architecture
* Interactive workflow design
* Minimal dependency approach
* Expandable frontend structure

---

# Current Status

Currently operational:

* Real API-connected dashboard
* Historical market visualization
* Live cargo value calculation
* Interactive chart system
* Multi-tab frontend architecture
* Real EVE market data integration
* Dynamic chart interaction workflow

The dashboard has evolved from standalone frontend utilities into a connected market analysis platform.

---

# Planned Features

* Regional market comparison
* Moving averages
* Volatility indicators
* Buy/Sell pressure analysis
* AI-assisted market commentary
* Route risk integration
* Expanded analytics modules
