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

No direct public database access exists.

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
| `station_market_snapshots`  | Station-level live market snapshots |
| Kill-signal tables          | Gatecamp, Pochven and combat intelligence inputs |

---

# 🧱 Key Design Decisions

* Historical and live market data separated

  * different update frequencies and analytics use cases

* Incremental synchronization

  * avoids expensive full-region imports

* Multilingual item support

  * enables localized search and UI features

* Snapshot-based analytics

  * supports liquidity, spread, and trade analysis

* Retention for high-volume tables

  * prevents live snapshot and global price tables from growing without operational limits

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

This enables multilingual item lookup and localized frontend functionality.

---

# 📈 Current Dataset Scale

| Metric              | Approximate Size |
| ------------------- | ---------------- |
| Indexed Items       | ~16,800          |
| Historical Records  | ~848,000         |
| Supported Languages | 8                |
| Trade Hubs          | 5                |

High-volume production tables are managed through pruning jobs rather than being allowed to grow indefinitely. This became important after an operational review found that overlapping scheduled workers had produced more than 100 million unnecessary rows.

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
* Retention-managed market price storage
* Worker execution tracking
* Live kill-signal storage for route, Pochven and gatecamp tools
* Multilingual item search
* Dashboard data delivery
* Trade analysis support
* Charting data source
* Trade Looper data source

---

# 📈 Current Status

**Live Production Database**

Supports:

* Historical analytics
* Market charting
* Trade intelligence
* Localization services
* Snapshot aggregation
* Dashboard integrations

Platform URL:

https://eve-tradelooper.com/
