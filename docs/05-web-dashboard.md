# 05 – Public Web Dashboard

## Objective

Provide a browser-based interface for EVE market analytics and player-facing tools.

The dashboard turns the backend data pipeline into a usable product by connecting real market data, API responses, and interactive frontend features.

---

## Current Core Features

* Cargo value calculator with EVE copy/paste input
* Trade Helper tools
* Profit calculator
* Buy Order calculator
* Cargo space tools
* Interactive item price charts
* Clickable item results
* Multi-tab interface
* Dynamic chart tabs
* Time range selection
* Responsive dark UI
* Read-only access to market data

---

## Architecture Model

User → Frontend → API → PostgreSQL

Future public deployment model:

User → Reverse Proxy → Frontend → API → PostgreSQL

---

## UI Structure

### Main Tabs

* Cargo
* Trade Helper
* Charts

### Chart Sub-Tabs

The Charts section supports dynamically opened chart tabs.

Current behavior:

* Clicking an item in the Cargo result opens a chart tab
* Multiple chart tabs can stay open at the same time
* Chart tabs can be closed individually
* Chart view receives focus automatically when opened

---

## Cargo Calculator

The Cargo Calculator supports direct copy/paste input from EVE Online.

### Current Capabilities

* Parses item names and quantities
* Handles tab-separated input
* Detects invalid lines
* Detects items not found in the database
* Calculates total ISK value
* Formats values for readability
* Provides clickable item results for chart navigation

### Example Input

```
Compressed Plagioclase    619164
Vermillion Mykoserocin    240
Compressed Veldspar       9665
```

---

## Trade Helper

The Trade Helper integrates several smaller trading utilities into the dashboard.

### Current Tools

* Cargo calculator
* Profit calculator
* Buy Order calculator
* Cargo space tools

### Purpose

These tools support quick trading and hauling decisions without requiring direct database access or manual spreadsheet work.

---

## Interactive Charts

The dashboard supports historical price visualization for selected items.

### Current Chart Features

* Item price history visualization
* Average price line
* Adjusted price line
* Time range selection
* Multiple open charts
* Closable chart tabs
* Automatic focus behavior

### Statistics Cards

Each chart can show basic price statistics:

* Latest price
* Minimum price
* Maximum price
* Percentage change

---

## Data Flow

Frontend queries the API and receives structured JSON responses.

### Flow

Frontend input → API request → Database query → API response → UI rendering

### Design Principles

* No direct database access from the frontend
* API performs all data transformations
* Frontend focuses on interaction and presentation
* Backend remains responsible for correctness of calculations

---

## Current Status

Frontend implementation is now functional.

* Cargo Calculator connected to real API data
* Trade Helper integrated into the interface
* Interactive Charts implemented
* Multi-tab system operational
* Dynamic chart tabs working
* API integration confirmed
* Real EVE market data displayed in the UI

---

## Known Limitations

* No public reverse proxy yet
* No HTTPS/domain setup yet
* Frontend styling is functional but still early
* No user accounts or saved preferences
* No advanced market indicators yet
* No regional market comparison yet

---

## Next Steps

* Improve visual polish and layout consistency
* Add public reverse proxy and HTTPS
* Expand chart analytics
* Add regional market analysis
* Add volatility indicators
* Add moving averages
* Prepare screenshots and demo GIFs for GitHub
