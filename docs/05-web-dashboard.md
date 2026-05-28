# 05 – Public Web Dashboard

Browser-based interface for the EVE Market Platform.

The dashboard combines market analytics, historical data, trading utilities, route intelligence, and visualization systems into a single user-facing application.

---

# 🎯 Purpose

Provide a unified interface for market analysis, trading decisions, logistics planning, and operational insights.

---

# 🏗️ Architecture

### Current

```text
Browser
    ↓
Frontend
    ↓
FastAPI
    ↓
PostgreSQL
```

### Planned Public Deployment

```text
Browser
    ↓
Reverse Proxy
    ↓
Frontend
    ↓
FastAPI
    ↓
PostgreSQL
```

---

# 🛠️ Dashboard Modules

| Module               | Purpose                       |
| -------------------- | ----------------------------- |
| Cargo Value          | Inventory valuation           |
| Market Charts        | Historical analytics          |
| Trade Looper         | Arbitrage opportunities       |
| Logistics Calculator | Cargo and profit planning     |
| Hauling Intelligence | Route risk evaluation         |
| Wormhole Mapping     | Chain visualization           |
| Market Newsfeed      | Optional immersive news layer |
| WebGL Environment    | Real-time dashboard rendering |

---

# 🧱 Key Design Decisions

* Dashboard-first architecture

  * tools share a common interface

* API-driven communication

  * frontend remains lightweight

* Modular feature system

  * tools can evolve independently

* Persistent browser state

  * sessions survive refreshes

* Real EVE market data

  * no simulated datasets

---

# 📊 Core Capabilities

### Market Analytics

* Historical market charts
* Regional hub comparison
* Snapshot visualization
* Market search

### Trading Tools

* Cargo valuation
* Trade opportunity discovery
* Profit estimation
* Fee-aware calculations

### Logistics

* Route evaluation
* Cargo planning
* Wormhole mapping
* Transport analysis

### Platform Features

* Multilingual item support
* Dynamic chart tabs
* Persistent sessions
* Responsive interface

---

# 🌍 Supported Trade Hubs

* Jita / The Forge
* Amarr / Domain
* Dodixie / Sinq Laison
* Hek / Metropolis
* Rens / Heimatar

---

# 🚀 Data Flow

```text
User Action
      ↓
Frontend Module
      ↓
FastAPI Endpoint
      ↓
Market Database
      ↓
Analytics Response
      ↓
Interactive Visualization
```

---

# ⚙️ Technology Stack

* JavaScript
* HTML5
* CSS3
* Chart.js
* Three.js
* FastAPI
* PostgreSQL

---

# 📈 Current Status

**Operational**

* Market dashboard
* Historical analytics
* Cargo valuation
* Trade Looper
* Route analysis foundation
* Wormhole mapping
* WebGL rendering layer
* Multilingual item support

---

# ⚠️ Current Limitations

* No public HTTPS deployment
* No reverse proxy layer
* No account system
* No cloud synchronization
* Limited observability

---

# 🔮 Planned Expansion

* Reverse proxy & HTTPS
* Advanced market analytics
* Enhanced route intelligence
* Additional dashboard modules
* Public deployment hardening
* Azure-connected infrastructure
