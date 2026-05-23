# 05 – Public Web Dashboard

## Objective

The web dashboard provides browser-based access to EVE market analytics and trading tools.

It connects the backend API, historical database, and interactive frontend features into a usable interface.

---

## Current Features

- Cargo value calculator
- Trade helper tools
- Profit calculator
- Buy order calculator
- Cargo space tools
- Interactive price charts
- Multi-tab interface
- Dynamic chart tabs
- Time range selection
- Responsive dark UI

---

## Architecture

```text
User → Frontend → API → PostgreSQL
```

Planned public deployment:

```text
User → Reverse Proxy → Frontend → API → PostgreSQL
```

---

## Main UI Sections

### Cargo

Supports direct EVE copy/paste input.

Current capabilities:

- Item and quantity parsing
- Invalid line detection
- Missing item detection
- Total ISK calculation
- Clickable item results
- API-connected live pricing

Example input:

```text
Compressed Plagioclase    619164
Vermillion Mykoserocin    240
Compressed Veldspar       9665
```

---

### Trade Helper

Integrated trading utilities:

- Cargo calculator
- Profit calculator
- Buy order calculator
- Cargo space tools

The goal is to provide lightweight trading support directly inside the browser interface.

---

### Charts

Interactive historical market charts.

Current features:

- Historical price visualization
- Average and adjusted price display
- Dynamic chart tabs
- Multiple open charts
- Closable tabs
- Automatic focus behavior
- Time range selection

### Statistics

Each chart can display:

- Latest price
- Minimum price
- Maximum price
- Percentage change

---

## Data Flow

```text
Frontend → API → Database → API → Frontend
```

### Design Principles

- No direct database access
- API handles calculations and transformations
- Frontend focuses on interaction and visualization

---

## Current Status

Currently operational:

- Cargo calculator connected to live API data
- Trade Helper integrated
- Interactive charts functional
- Multi-tab frontend system working
- Dynamic chart tabs implemented
- Real EVE market data displayed in browser

---

## Known Limitations

- No public reverse proxy yet
- No HTTPS/domain setup
- Styling still early-stage
- No user accounts or preferences
- No advanced analytics yet
- No regional comparison tools

---

## Next Steps

- Improve UI polish and consistency
- Add reverse proxy and HTTPS
- Expand chart analytics
- Add regional market comparison
- Add moving averages and indicators
- Prepare screenshots and demo material for GitHub
