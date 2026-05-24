# 05 – Public Web Dashboard

## Objective

The web dashboard provides browser-based access to EVE market analytics, historical pricing data, and trading tools.

It connects the backend API, historical database, and interactive frontend systems into a modular browser-based interface.

---

## Current Features

- Cargo value calculator
- Trade helper tools
- Interactive historical charts
- Regional market selection
- Multilingual item support
- Multi-tab dashboard system
- Dynamic chart tabs
- Persistent chart sessions
- Responsive dark UI
- Route risk analysis foundation

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

### Cargo Value

Supports direct EVE copy/paste input.

Current capabilities:

- Item and quantity parsing
- Invalid line detection
- Missing item detection
- Total ISK calculation
- Clickable item results
- API-connected live pricing
- Direct chart integration

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

The goal is to provide lightweight trading and hauling support directly inside the dashboard.

---

### Charts

Interactive historical market charts connected to stored regional history data.

Current features:

- Historical price visualization
- Average and adjusted price display
- Regional market selection
- Dynamic chart tabs
- Multiple open charts
- Closable chart tabs
- Persistent chart sessions
- Automatic history backfill
- Time range selection
- Chart tooltip analytics

### Chart Analytics

Current chart analytics include:

- Average price
- Low/high values
- Daily traded volume
- Order count
- Percentage change

### Interaction Features

- Mouse-wheel zoom
- Drag-select zoom
- Reset zoom controls
- Automatic tab focus behavior

---

### Route Risk

Early frontend foundation for future hauling and route analysis systems.

Current prototype includes:

- Route setup UI
- Risk display system
- Basic scoring prototype
- API integration preparation

---

## Multilingual Item Support

The dashboard supports official localized EVE item names.

Currently supported:

- English
- German
- French
- Spanish
- Russian
- Japanese
- Korean
- Simplified Chinese

This allows localized item search instead of English-only item naming.

---

## Data Flow

```text
Frontend → API → Database → API → Frontend
```

### Design Principles

- No direct database access
- API handles calculations and transformations
- Frontend focuses on interaction and visualization
- Modular tab-based architecture

---

## Current Status

Currently operational:

- Cargo Value connected to live API data
- Historical regional market charts functional
- Trade Helper integrated
- Dynamic multi-chart system active
- Persistent chart sessions working
- Real EVE market data displayed in browser
- Multilingual item support active
- Route Risk foundation started

---

## Known Limitations

- No public reverse proxy yet
- No HTTPS/domain setup
- Styling still evolving
- No user accounts or cloud sync
- No advanced AI analytics yet
- Route Risk still early-stage

---

## Next Steps

- Improve UI polish and consistency
- Add reverse proxy and HTTPS
- Expand chart analytics
- Improve route risk scoring
- Add moving averages and indicators
- Prepare demo screenshots and GIFs
- Continue modular frontend expansion
