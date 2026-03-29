# 03 – Database Layer

## Objective

Provide a persistent relational data store for application services.

The database layer stores structured market data, item metadata, and import execution logs used by the API and worker services.

---

## Technology Stack

- PostgreSQL 16
- Docker container deployment
- Named Docker volume for persistence

---

## Architecture Concept

The database runs as an internal container service inside the Docker Compose stack.

### Access Model

API container → PostgreSQL → persistent volume  
Worker container → PostgreSQL → persistent volume

### Key Design Decisions

- Database is not exposed to LAN or public networks
- All access is routed through controlled services (API / Worker)
- Optimized for read-heavy analytical queries

---

## Data Scope

The database stores structured EVE Online market data.

### Core Data Domains

- Item metadata
- Global market prices (ESI)
- Regional market history
- Import execution tracking

---

## Current Schema

### Tables

- `item_types`
- `esi_market_prices`
- `region_market_history`
- `price_import_runs`

---

### `item_types`

Reference table for all known EVE item types.

**Purpose**

- Provide human-readable item names
- Enable joins with market data

**Fields (typical)**

- `type_id` (primary key)
- `type_name`

---

### `esi_market_prices`

Stores global price snapshots from the EVE ESI API.

**Purpose**

- Fast access to current average prices
- Used for cargo value calculations

**Fields (typical)**

- `type_id`
- `average_price`
- `adjusted_price`

---

### `region_market_history`

Stores time-series market data per region.

**Purpose**

- Historical analysis
- Graph visualization
- Trend detection

**Fields (typical)**

- `type_id`
- `region_id`
- `date`
- `average`
- `highest`
- `lowest`
- `volume`

---

### `price_import_runs`

Tracks execution of worker import processes.

**Purpose**

- Debugging and traceability
- Performance tracking of imports

**Fields (typical)**

- `id`
- `source`
- `started_at`
- `finished_at`
- `status`
- `notes`

---

## Indexing Strategy

Indexes are applied to support:

- Fast lookup by `type_id`
- Time-based queries on historical data
- Efficient joins between item and market tables

---

## Security Considerations

- No host port exposure
- Internal Docker network only
- Credentials injected via environment variables
- API acts as controlled read layer
- Worker acts as controlled write layer

---

## Current Status

- PostgreSQL container operational
- Persistent volume active
- Schema extended beyond test data
- Real EVE data successfully ingested
- Read/write operations validated across services

---

## Validation Performed

- API → DB connectivity confirmed
- Worker → DB write operations confirmed
- JOIN queries validated (item + price data)
- Historical data queries tested

---

## Known Limitations

- No migration framework yet
- No partitioning for large datasets
- Index tuning still basic
- Data retention strategy not defined

---

## Next Steps

- Introduce schema migrations (Alembic or similar)
- Optimize indexing based on query patterns
- Evaluate partitioning for large time-series tables
- Define long-term storage and cleanup strategy
