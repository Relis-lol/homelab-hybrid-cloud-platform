# 03 – Database Layer

## Objective

Provide a persistent relational data store for application services.

The database layer stores structured market data, import metadata, and historical records used by the application and worker services.

---

## Technology Stack

- PostgreSQL 16
- Docker container deployment
- Named Docker volume for persistence

---

## Architecture Concept

The database runs as an internal container service inside the Docker Compose stack.

### Access Model

API container → PostgreSQL container → persistent volume  
Worker container → PostgreSQL container → persistent volume

### Key Design Decisions

- Database remains internal to the Docker network
- No direct LAN or public access
- Application and worker services control all data access

---

## Data Scope

The database stores structured market data related to EVE Online market analysis.

### Primary Use Cases

- EVE Online market price history
- Item type metadata
- Timestamped price records
- Import run tracking

---

## Initial Schema

Current core tables:

- `item_types`
- `market_prices`
- `price_import_runs`

### Table Roles

#### `item_types`

Stores item reference metadata used by the application.

Typical contents:

- Item identifier (`type_id`)
- Item name (`type_name`)

This table acts as a lookup reference for market data.

---

#### `market_prices`

Stores timestamped historical market data.

Typical contents:

- Item identifier
- Region identifier
- Price timestamp
- Average price
- Lowest price
- Highest price
- Traded volume

This table is designed for time-series style queries.

Indexes were added to support efficient queries by item, region, and timestamp.

---

#### `price_import_runs`

Tracks execution of background import processes.

Typical contents:

- Import run identifier
- Import source
- Start timestamp
- Finish timestamp
- Execution status
- Optional notes

This table provides traceability and debugging visibility for data import jobs.

---

## Security Considerations

- Database not exposed via host ports
- Access restricted to the Docker network
- Credentials provided through container environment variables
- API layer acts as the controlled read interface
- Worker layer acts as the controlled write/import interface

---

## Current Status

- PostgreSQL container deployed
- Named Docker volume active for persistence
- Initial schema created
- Database verified through direct container access
- Database verified through API connection testing
- Read operations confirmed through API endpoints
- Write operations confirmed through seed endpoint
- Worker-based import run logging confirmed

---

## Validation Performed

The following database-related checks were successfully completed:

- Database connectivity verified through `/db-check`
- Test data insertion via `/seed-test-data`
- Item retrieval via `/items`
- Price retrieval via `/prices`
- Import history retrieval via `/import-runs`

These tests confirm that both application-level read operations and worker-driven write operations function correctly.

---

## Next Steps

- Define stricter schema conventions for future imports
- Introduce a migration strategy for schema evolution
- Prepare ingestion of a larger item catalog
- Replace test data with real EVE market data
- Extend indexing strategy once query patterns are known
