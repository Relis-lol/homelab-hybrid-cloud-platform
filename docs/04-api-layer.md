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

  * calculations remain consistent across tools

* JSON-based communication

  * lightweight integration for browser clients

* Database abstraction layer

  * backend controls validation and filtering

* Modular endpoint design

  * supports independent feature growth

---

# 📦 Core Capabilities

### Market Data

* Item metadata lookup
* Multilingual search
* Global ESI prices
* Historical market access
* Regional market analytics

### Dashboard Services

* Cargo valuation
* Historical charting
* Market search
* Snapshot retrieval
* Trade analytics

### Platform Services

* Health monitoring
* Database validation
* Import tracking
* Worker integration

---

# 📊 Major Endpoint Groups

| Area                  | Purpose              |
| --------------------- | -------------------- |
| Health                | Runtime validation   |
| Items                 | Search and metadata  |
| Market History        | Historical analytics |
| Cargo Value           | Cargo pricing        |
| Regional Snapshots    | Live market state    |
| Trade Recommendations | Arbitrage analysis   |
| Import Runs           | Worker tracking      |
| Route Analysis        | Risk evaluation      |

---

# 🌍 Market Coverage

Supported trade hubs:

* Jita / The Forge
* Amarr / Domain
* Dodixie / Sinq Laison
* Hek / Metropolis
* Rens / Heimatar

Returned analytics may include:

* Average prices
* High / low prices
* Trade volume
* Order counts
* Market spreads
* Snapshot data

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

# ⚙️ Processing Logic

Current API responsibilities include:

* Market aggregation
* Historical filtering
* Snapshot processing
* Cargo calculations
* Trade recommendation generation
* Item translation lookup
* Dashboard data delivery
* Frontend response formatting

---

# 🚀 Frontend Integrations

Connected modules:

* Market Dashboard
* Trade Looper
* Logistics Calculator
* Hauling Intelligence
* Historical Charts
* Market Search

---

# 🔐 Security Model

* No direct database exposure
* FastAPI input validation
* Internal container communication
* Firewall-restricted host access
* Backend-controlled data access

---

# 📈 Current Status

**Operational**

* FastAPI application layer
* Historical market analytics
* Snapshot APIs
* Cargo valuation services
* Trade recommendation system
* Multilingual search
* Worker integration
* Dashboard integration

---

# ⚠️ Current Limitations

* No authentication
* No rate limiting
* No caching layer
* Partial response-model coverage
* Limited pagination support

---

# 🔮 Planned Expansion

* Response model standardization
* Advanced filtering
* Query caching
* Pagination improvements
* API performance optimization
* Expanded market analytics
* Public deployment hardening
