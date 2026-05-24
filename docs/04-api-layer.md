# 04 – API Layer

## Objective

The API provides a controlled access layer between clients and the PostgreSQL database.

It handles market queries, historical analytics, business logic, and frontend-facing responses for the dashboard platform.

---

## Stack

- Python
- FastAPI
- Uvicorn
- PostgreSQL (psycopg)
- Docker deployment

---

## Architecture

```text
Client → API → PostgreSQL
```

### Core Principles

- No direct database access
- Centralized query handling
- Controlled and validated responses
- API-driven frontend communication

---

## Current Features

- Item lookup and multilingual search
- Global ESI market price retrieval
- Regional historical market access
- Cargo value calculation
- Historical chart support
- Import run tracking
- Route risk analysis foundation

---

## Main Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/health` | Health check |
| `GET` | `/db-check` | Database validation |
| `GET` | `/items` | Item metadata |
| `GET` | `/items/search?q=` | Item search |
| `GET` | `/esi/global-prices` | Global market prices |
| `GET` | `/market-history` | Historical market data |
| `POST` | `/cargo/value` | Cargo value calculation |
| `GET` | `/import-runs` | Worker execution history |
| `POST` | `/route-risk/analyze` | Route risk prototype |

---

## Regional Market Support

Historical market endpoints currently support:

- Jita / The Forge
- Amarr / Domain
- Dodixie / Sinq Laison
- Hek / Metropolis
- Rens / Heimatar

Returned data includes:

- Average prices
- Low/high values
- Traded volume
- Order counts

---

## Multilingual Item Support

The API supports official localized EVE item names.

### Current Supported Languages

- English
- German
- French
- Spanish
- Russian
- Japanese
- Korean
- Simplified Chinese

This enables multilingual item lookup and localized frontend search behavior.

---

## Current Processing Logic

The API currently handles:

- JOIN queries between item and market tables
- Historical regional filtering
- Cargo value aggregation
- Auto-backfill handling for missing history
- Frontend-ready JSON responses
- Basic route risk scoring prototype

---

## Frontend Integration

The API acts as the primary backend for the browser dashboard.

Current frontend integrations include:

- Cargo Value
- Historical Charts
- Market Search
- Regional Market Selection
- Route Risk foundation

---

## Security Model

- No public database exposure
- Input validation via FastAPI
- Firewall-restricted access
- API acts as controlled read layer

---

## Current Status

Currently operational:

- Stable FastAPI application layer
- Connected to real EVE market data
- Regional history system active
- Multilingual item support active
- Multi-endpoint architecture operational
- Worker integration confirmed
- Frontend dashboard integration functional

---

## Known Limitations

- No authentication system
- No rate limiting
- No caching layer
- No pagination for large datasets
- Response schemas still incomplete
- Route risk scoring still early-stage

---

## Next Steps

- Add response models
- Improve filtering and pagination
- Introduce caching
- Optimize chart query performance
- Expand route risk scoring logic
- Prepare public deployment hardening
