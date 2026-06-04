# 05 – Public Web Dashboard

Browser-based interface for the EVE Trade Intelligence Platform.

The dashboard combines market analytics, historical data, trading tools, route intelligence, visualization systems, and platform services into a single user-facing application.

---

# 🎯 Purpose

Provide a unified interface for market analysis, trading decisions, logistics planning, and operational insights.

---

# 🏗️ Architecture

```text
Browser
    ↓
Frontend
    ↓
FastAPI
    ↓
PostgreSQL
```

### Live Deployment

```text
Browser
    ↓
Cloudflare
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
| AHN News Network     | Dynamic news aggregation      |
| WebGL Environment    | Real-time dashboard rendering |

---

# 🧱 Key Design Decisions

* Dashboard-first architecture

  * tools share a unified interface

* API-driven communication

  * frontend remains lightweight

* Modular feature system

  * features evolve independently

* Persistent browser state

  * sessions survive refreshes

* Real EVE market data

  * analytics are based on live and historical datasets

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
* WebGL environment
* AHN News Network

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

**Live Production Platform**

* Market dashboard
* Historical analytics
* Cargo valuation
* Trade Looper
* Hauling Intelligence
* Wormhole Mapping
* AHN News Network
* WebGL rendering layer
* Multilingual item support

Platform URL:

https://eve-tradelooper.com/

---

# 🎯 Engineering Focus

The dashboard serves as the primary user interface for all analytics systems and integrates market intelligence, visualization, trading tools, logistics workflows, and operational data into a single platform experience.
