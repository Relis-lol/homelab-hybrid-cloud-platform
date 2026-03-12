# 03 – Database Layer

## Objective

Provide a persistent relational data store for application services.

The database layer is responsible for storing structured market data, import metadata, and historical records used by the application.

---

## Technology Stack

- PostgreSQL 16
- Docker container deployment
- Named Docker volume for persistence

---

## Architecture Concept

The database runs as an internal container service inside the Docker stack.

### Access Model

**API container → PostgreSQL container → persistent volume**  
**Worker container → PostgreSQL container → persistent volume**

### Key Design Decisions

- Database remains internal to the Docker network
- No direct LAN or public access
- Application and worker layers control all data access

---

## Data Scope

The database is designed to store structured market data.

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

Stores item reference data used by the application.

Typical contents:

- Item identifier
- Item name

#### `market_prices`

Stores timestamped market history records.

Typical contents:

- Item reference
- Region identifier
- Price timestamp
- Average price
- Low price
- High price
- Traded volume

#### `price_import_runs`

Tracks background import execution.

Typical contents:

- Run identifier
- Import source
- Start timestamp
- Finish timestamp
- Status
- Notes

Indexes were added to support historical query performance.

---

## Security Considerations

- Database not exposed via host port
- Access restricted to the Docker network
- Credentials provided through container environment variables
- API layer acts as the controlled read interface
- Worker layer acts as the controlled write/import interface

---

## Current Status

- PostgreSQL container deployed
- Named volume active for persistence
- Initial schema created
- Database verified through direct container access
- Database verified through API connection testing
- Read operations confirmed through API endpoints
- Write operations confirmed through seed endpoint
- Worker-based import run logging confirmed

---

## Validation Performed

The following database-related checks were successfully completed:

- Connection check through `/db-check`
- Insert test data through `/seed-test-data`
- Read item data through `/items`
- Read price data through `/prices`
- Read import run history through `/import-runs`

This confirms that both application-level reads and worker-related writes already function correctly.

---

## Next Steps

- Define stricter schema conventions for future imports
- Add a migration strategy for schema evolution
- Prepare larger item catalog ingestion
- Store real EVE market data instead of test records
- Extend indexing strategy once query patterns grow
