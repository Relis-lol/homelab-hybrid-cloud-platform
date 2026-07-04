# 04 – API Layer

FastAPI application layer connecting frontend systems, worker services, and market analytics data.

The API provides validated access to historical market datasets, real-time snapshots, trading analytics, and platform services while keeping the database isolated from direct client access.

---

# 🎯 Purpose

Serve market intelligence, analytics, and platform functionality through a centralized backend interface.

---

# 🛠️ Stack

| Component       | Technology |
| --------------- | ---------- |
| Framework       | FastAPI    |
| Runtime         | Uvicorn    |
| Language        | Python     |
| Database Access | psycopg    |
| Deployment      | Docker     |

---

# 🏗️ Architecture

```text
Browser
    ↓
FastAPI
    ↓
PostgreSQL

Worker
    ↓
FastAPI
    ↓
PostgreSQL
```

---

# 🧱 Key Design Decisions

* API-first architecture

  * frontend never accesses the database directly

* Centralized business logic

  * calculations remain consistent across all tools

* JSON-based communication

  * lightweight integration for browser clients

* Database abstraction layer

  * validation and filtering remain server-side

* Modular endpoint design

  * features can evolve independently

---

# 📦 Core Capabilities

### Market Data

* Item metadata lookup
* Multilingual search
* Global ESI prices
* Historical market access
* Regional market analytics

### Analytics Services

* Cargo valuation
* Historical charting
* Snapshot retrieval
* Hub snapshot aggregation
* Trade recommendations
* Route intelligence

### Platform Services

* Health monitoring
* Database validation
* Import tracking
* Worker integration

---

# 📊 Major Endpoint Groups

| Area                  | Purpose                    |
| --------------------- | -------------------------- |
| Health                | Runtime validation         |
| Items                 | Search and metadata        |
| Market History        | Historical analytics       |
| Cargo Value           | Cargo pricing              |
| Regional Snapshots    | Live market state          |
| Hub Snapshots         | Live trade-hub aggregation |
| Trade Recommendations | Arbitrage analysis         |
| Import Runs           | Worker tracking            |
| Route Analysis        | Risk evaluation            |
| Gatecamp Intelligence | Live route danger signals  |
| Pochven Intelligence  | Flashpoint and Trig activity |
| ESS / Gank Tools      | Combat and robbery calculators |
| Wiki                  | Static reference content delivery |

---

# 🌍 Market Coverage

Supported trade hubs:

* Jita / The Forge
* Amarr / Domain
* Dodixie / Sinq Laison
* Hek / Metropolis
* Rens / Heimatar

Returned analytics include:

* Average prices
* High / low prices
* Trade volume
* Order counts
* Market spreads
* Snapshot data
* Trade opportunity metrics

---

# 🌐 Localization Support

Supported languages:

* English
* German
* French
* Spanish
* Russian
* Japanese
* Korean
* Simplified Chinese

Used for multilingual item lookup and localized frontend search.

---

# ⚙️ Processing Responsibilities

Current API responsibilities include:

* Market aggregation
* Historical filtering
* Snapshot processing
* Hub snapshot aggregation
* Market-quality filtering
* Cargo calculations
* Trade recommendation generation
* ESS raid estimates
* Gank profitability estimates
* Pochven and Triglavian activity summaries
* Item translation lookup
* Dashboard data delivery
* Frontend response formatting

---

# 🚀 Frontend Integrations

Connected systems:

* Market Dashboard
* Trade Looper
* Hauling Intelligence
* Historical Charts
* Market Search
* AHN News Network

---

# 🔐 Security Model

* No direct database exposure
* FastAPI input validation
* Internal container communication
* Backend-controlled data access
* Environment-based configuration
* Generic client-facing error responses for production failures

Server-side logs keep exception details for troubleshooting, while API clients receive generic failure messages instead of raw stack or exception text.

---

# 📈 Current Status

**Live Production API**

* Historical market analytics
* Snapshot APIs
* Hub snapshot aggregation
* Cargo valuation services
* Trade recommendation engine
* Multilingual search
* Worker integration
* Dashboard integration
* Route analysis services
* Gatecamp intelligence
* Pochven / Trig activity services
* ESS and gank calculator support
* Wiki content integration

Platform URL:

https://eve-tradelooper.com/

---

# 🎯 Engineering Focus

The API acts as the central orchestration layer between market ingestion, analytics processing, data storage, and frontend delivery.

All market calculations, trade intelligence, filtering, and aggregation logic are executed server-side to ensure consistency across platform features.
