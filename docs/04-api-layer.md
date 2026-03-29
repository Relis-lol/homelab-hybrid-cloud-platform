# 04 – API Layer

## Objective

Provide a controlled application layer between the database and external consumers.

The API handles structured data access, query logic, and business-level transformations.

---

## Technology Stack

- Python FastAPI
- Docker container deployment
- Uvicorn ASGI server
- PostgreSQL via `psycopg`

---

## Architecture Concept

Client → API → PostgreSQL

---

## Responsibilities

- Request validation
- Data aggregation and transformation
- Controlled database access
- JSON response formatting

---

## Current Capabilities

The API has moved beyond test endpoints and now exposes real application functionality.

### Core Features

- Item lookup and search
- Global price retrieval (ESI)
- Regional market history access
- Cargo value calculation (multi-item input)
- Import run tracking

---

## Available Endpoints

### `GET /health`

Service health check.

---

### `GET /db-check`

Database connectivity validation.

---

### `GET /items`

Returns item metadata.

---

### `GET /items/search?q=...`

Case-insensitive item search.

---

### `GET /esi/global-prices`

Returns current global price data.

---

### `GET /market-history?type_id=...&region_id=...`

Returns historical market data.

---

### `POST /cargo/value`

Calculates total cargo value.

**Input**

- List of item IDs and quantities

**Output**

- Total estimated value based on current prices

---

### `GET /import-runs`

Returns import execution history.

---

## Business Logic Layer

The API now performs:

- JOIN operations between item metadata and price tables
- Aggregation of multi-item cargo values
- Filtering of historical data by item and region

---

## Security Model

- No direct DB exposure
- Controlled query surface
- Input validation via FastAPI
- LAN-restricted access via firewall

---

## Current Status

- Fully operational application layer
- Connected to real market data
- Multi-endpoint API available
- Worker integration confirmed

---

## Known Limitations

- No authentication
- No rate limiting
- No pagination
- No response schemas (Pydantic models incomplete)
- No caching layer

---

## Next Steps

- Add response models
- Introduce pagination and filtering
- Add caching (Redis or similar)
- Prepare API for public exposure
- Add structured response models
- Introduce filtering for market queries
- Separate test-only endpoints from production-facing endpoints
- Prepare API design for frontend consumption
- Integrate real EVE market import output from worker processes
