# 03 – Database Layer

PostgreSQL data platform powering market analytics, historical storage, localization, snapshot tracking, and backend services.

The database acts as the central source of truth for all market intelligence, dashboard analytics, and worker-generated datasets.

---

# 🎯 Purpose

Store, organize, and serve historical and real-time market data for analytics, visualization, and trading tools.

---

# 🛠️ Stack

| Component       | Technology                 |
| --------------- | -------------------------- |
| Database Engine | PostgreSQL 16              |
| Deployment      | Docker Container           |
| Storage         | Persistent Docker Volume   |
| Access          | Internal Container Network |

---

# 🏗️ Architecture

```text
Frontend
    ↓
FastAPI
    ↓
PostgreSQL
    ↑
Worker Services
```

Database access remains internal to the Docker network.

No direct LAN or public database access exists.

---

# 📦 Core Tables

| Table                       | Purpose                   |
| --------------------------- | ------------------------- |
| `item_types`                | Item metadata             |
| `item_name_translations`    | Localized item names      |
| `esi_market_prices`         | Global ESI prices         |
| `region_market_history`     | Historical market data    |
| `regional_market_snapshots` | Intraday market snapshots |
| `hourly_snapshot_items`     | Snapshot tracking targets |
| `regional_order_sync_state` | Incremental sync tracking |
| `price_import_runs`         | Worker execution history  |

---

# 🧱 Key Design Decisions

* Historical and live market data separated

  * different update frequencies and use cases

* Incremental synchronization

  * avoids expensive full-region imports

* Multilingual item support

  * enables localized search and UI features

* Snapshot-based analytics

  * supports future liquidity and trend systems

* Internal-only database access

  * reduces exposure and simplifies security

---

# 📊 Market Coverage

Supported trade hubs:

* Jita / The Forge
* Amarr / Domain
* Dodixie / Sinq Laison
* Hek / Metropolis
* Rens / Heimatar

Stored data includes:

* Average prices
* Highest prices
* Lowest prices
* Order counts
* Trade volume
* Market spreads
* Buy and sell liquidity

---

# 🌍 Localization System

Official EVE item translations are stored locally.

### Supported Languages

* English
* German
* French
* Spanish
* Russian
* Japanese
* Korean
* Simplified Chinese

This allows multilingual item lookup and localized frontend experiences.

---

# 📈 Current Dataset Scale

| Metric              | Approximate Size |
| ------------------- | ---------------- |
| Indexed Items       | ~16,800          |
| Historical Records  | ~848,000         |
| Supported Languages | 8                |
| Trade Hubs          | 5                |

---

# 🔐 Security Model

* Internal Docker network only
* No exposed database ports
* Environment-based credentials
* API-controlled read access
* Worker-controlled write access

---

# 🚀 Current Capabilities

* Historical market storage
* Regional market analytics
* Snapshot collection
* Worker execution tracking
* Multilingual item search
* Dashboard data delivery
* Trade analysis support
* Charting data source

---

# ⚠️ Current Limitations

* No migration framework
* Limited indexing strategy
* No table partitioning
* No time-series optimization
* Snapshot retention still evolving

---

# 🔮 Planned Expansion

* Migration tooling
* Advanced indexing
* Time-series partitioning
* Retention automation
* Query optimization
* Liquidity analytics
* Market anomaly datasets
