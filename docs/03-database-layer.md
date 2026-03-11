# 03 – Database Layer

## Objective

Provide a persistent relational data store for application services.

The database layer is responsible for storing structured market data and historical records used by the application.

---

## Technology Stack

- PostgreSQL 16
- Docker container deployment
- Named Docker volume for persistence

---

## Architecture Concept

The database runs as an internal container service inside the Docker stack.

Access model:

API container → PostgreSQL container → persistent volume

Key design decisions:

- database remains internal to Docker network
- no direct LAN or public access
- application layer controls all data access

---

## Data Scope

The database is designed to store structured market data.

Primary use cases:

- EVE Online market price history
- item type metadata
- timestamped price records
- import run tracking

---

## Initial Schema

Current core tables:

- `item_types`
- `market_prices`
- `price_import_runs`

Indexes added to optimize historical queries.

---

## Security Considerations

- database not exposed via host port
- access restricted to Docker network
- credentials provided through container environment variables
- API layer acts as controlled access interface

---

## Current Status

- PostgreSQL container deployed
- Named volume active for persistence
- Initial schema created
- Database verified via container connection
- Internal service communication functional

---

## Next Steps

- Connect API service to PostgreSQL
- Implement database queries in API layer
- Define import workflow for market data
- Expand schema for additional data sources
