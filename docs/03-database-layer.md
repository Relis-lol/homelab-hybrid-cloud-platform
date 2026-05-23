# 03 – Database Layer

## Objective

PostgreSQL acts as the persistent storage layer for market data, item metadata, and worker execution tracking.

The database is optimized for read-heavy analytics and historical market queries.

---

## Stack

- PostgreSQL 16
- Docker container deployment
- Persistent Docker volume

---

## Architecture

The database runs as an internal-only Docker service.

```text
API → PostgreSQL
Worker → PostgreSQL
````

Database access is restricted to internal container networking.
No direct LAN or public database exposure exists.

---

## Core Tables

| Table                   | Purpose                        |
| ----------------------- | ------------------------------ |
| `item_types`            | Item metadata and names        |
| `esi_market_prices`     | Global ESI market prices       |
| `region_market_history` | Historical regional price data |
| `price_import_runs`     | Worker execution tracking      |

---

## Current Capabilities

* Persistent historical market storage
* Fast item lookup by `type_id`
* Historical price tracking
* JOIN-based market analysis
* Worker execution traceability

---

## Current Status

* PostgreSQL container operational
* Persistent storage validated
* Real EVE market data imported
* API and worker integration confirmed
* Historical queries functioning

Current dataset scale:

* ~16,800 indexed item names
* ~848,000 historical market records

---

## Security Model

* Internal Docker network only
* No exposed database port
* Credentials handled via `.env`
* API handles controlled read access
* Worker handles controlled write access

---

## Known Limitations

* No migration framework yet
* Basic indexing only
* No partitioning strategy
* No retention policy defined

---

## Next Steps

* Add migration tooling
* Improve indexing strategy
* Evaluate time-series partitioning
* Define retention and cleanup workflows
