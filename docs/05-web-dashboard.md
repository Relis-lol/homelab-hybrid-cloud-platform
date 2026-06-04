# 05 – Public Web Dashboard

Browser-based interface for the EVE Trade Intelligence Platform.

The dashboard combines market analytics, historical data, trading tools, route intelligence, visualization systems, and platform services into a unified user-facing application.

---

# 🎯 Purpose

Provide a single interface for market analysis, trading decisions, logistics planning, and operational insights.

---

# 🏗️ Architecture

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

| Module | Purpose |
|---|---|
| Cargo Value | Inventory valuation |
| Market Charts | Historical analytics |
| Trade Looper | Arbitrage opportunities |
| Logistics Calculator | Cargo and profit planning |
| Hauling Intelligence | Route risk evaluation |
| Wormhole Mapping | Chain visualization |
| AHN News Network | Dynamic market news |
| WebGL Environment | Real-time dashboard rendering |
| Credits & Compliance | Legal notices and project information |

---

# 🧱 Key Design Decisions

* Dashboard-first architecture

  * all tools share a unified interface

* API-driven communication

  * frontend remains lightweight

* Modular feature system

  * features evolve independently

* Persistent browser state

  * sessions survive refreshes

* Real EVE market data

  * analytics are based on live and historical datasets

* No account requirements

  * tools remain accessible without registration

---

# 📊 Core Capabilities

### Market Analytics

* Historical market charts
* Regional hub comparison
* Snapshot visualization
* Market search
* Market trend analysis

### Trading Tools

* Cargo valuation
* Trade opportunity discovery
* Profit estimation
* Fee-aware calculations
* Liquidity evaluation

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
* Public HTTPS deployment

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

# 🌐 Public Deployment

The platform is publicly available through a production deployment hosted on a self-managed Linux server.

Deployment components include:

* Cloudflare DNS
* HTTPS encryption
* Reverse proxy protection
* Public domain integration
* Internal API architecture
* Internal-only database access

---

# ⚙️ Technology Stack

* JavaScript
* HTML5
* CSS3
* Chart.js
* Three.js
* FastAPI
* PostgreSQL
* Cloudflare

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
* Public web deployment

Platform URL:

https://eve-tradelooper.com/

---

# 🎯 Engineering Focus

The dashboard serves as the primary user interface for all analytics systems and integrates market intelligence, visualization, trading tools, logistics workflows, and operational data into a single platform experience.
