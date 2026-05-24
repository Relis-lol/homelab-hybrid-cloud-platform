# 03 – Database Layer

## Objective

PostgreSQL acts as the persistent storage layer for market data, item metadata, localization data, and worker execution tracking.

The database is optimized for read-heavy analytics, historical market queries, and API-driven frontend access.

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
```

Database access is restricted to internal container networking.

No direct LAN or public database exposure exists.

---

## Core Tables

| Table | Purpose |
|---|---|
| `item_types` | Base item metadata |
| `item_name_translations` | Official localized item names |
| `esi_market_prices` | Global ESI market prices |
| `region_market_history` | Historical regional market data |
| `price_import_runs` | Worker execution tracking |

---

## Current Capabilities

- Persistent historical market storage
- Regional market history tracking
- Multilingual item lookup support
- Fast lookup by `type_id`
- JOIN-based market analysis
- Historical chart data support
- Worker execution traceability

---

## Regional Market Support

Historical regional data currently includes:

- Jita / The Forge
- Amarr / Domain
- Dodixie / Sinq Laison
- Hek / Metropolis
- Rens / Heimatar

Stored market history includes:

- Daily average prices
- Low/high prices
- Order count
- Traded volume

---

## Multilingual Item System

Official localized EVE item names are supported through the `item_name_translations` table.

### Current Supported Languages

- English
- German
- French
- Spanish
- Russian
- Japanese
- Korean
- Simplified Chinese

This enables multilingual item search and localized frontend support.

---

## Current Status

- PostgreSQL container operational
- Persistent storage validated
- Real EVE market data imported
- Regional history pipeline operational
- Multilingual translation system active
- API and worker integration confirmed
- Historical queries functioning

Current dataset scale:

- ~16,800 indexed item names
- ~848,000 historical market records
- Official multilingual translations cached locally

---

## Security Model

- Internal Docker network only
- No exposed database port
- Credentials handled via `.env`
- API handles controlled read access
- Worker handles controlled write access

---

## Known Limitations

- No migration framework yet
- Basic indexing only
- No partitioning strategy
- No retention policy defined
- No dedicated time-series optimization yet

---

## Next Steps

- Add migration tooling
- Improve indexing strategy
- Evaluate time-series partitioning
- Define retention and cleanup workflows
- Optimize multilingual search performance
