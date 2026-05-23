# 04 – API Layer

## Objective

The API provides a controlled access layer between clients and the PostgreSQL database.

It handles market data queries, business logic, and frontend-facing responses.

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

- Item lookup and search
- Global ESI price retrieval
- Historical market data access
- Cargo value calculation
- Import run tracking

---

## Main Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/health` | Health check |
| `GET` | `/db-check` | Database validation |
| `GET` | `/items` | Item metadata |
| `GET` | `/items/search?q=` | Item search |
| `GET` | `/esi/global-prices` | Global market prices |
| `GET` | `/market-history` | Historical price data |
| `POST` | `/cargo/value` | Cargo value calculation |
| `GET` | `/import-runs` | Worker execution history |

---

## Current Processing Logic

The API currently handles:

- JOIN queries between item and market tables
- Multi-item cargo calculations
- Historical market filtering
- Frontend-ready JSON responses

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
- Multi-endpoint structure active
- Worker integration confirmed
- Frontend integration functional

---

## Known Limitations

- No authentication system
- No rate limiting
- No caching layer
- No pagination for large datasets
- Response schemas still incomplete

---

## Next Steps

- Add response models
- Improve filtering and pagination
- Introduce caching
- Separate test and production endpoints
- Optimize API responses for frontend usage
