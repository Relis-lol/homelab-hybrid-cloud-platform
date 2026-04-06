# 04 – API Layer

## Objective

Provide a controlled application layer between the database and external consumers.
The API handles structured data access, query logic, and business-level transformations.

---

## Technology Stack

* **Language:** Python
* **Framework:** FastAPI
* **Deployment:** Docker container
* **Server:** Uvicorn (ASGI)
* **Database Access:** psycopg (PostgreSQL)

---

## Architecture Concept

The API acts as the central access layer between clients and the database.

**Flow:**
Client → API → PostgreSQL (internal)

**Key Principles:**

* No direct database access from clients
* All queries are controlled and validated by the API
* Business logic is centralized in the API layer

---

## Responsibilities

* Request validation
* Data aggregation and transformation
* Controlled database access
* JSON response formatting

---

## Current Capabilities

The API has moved beyond test endpoints and now exposes real application functionality.

### Core Features

* Item lookup and search
* Global price retrieval (ESI)
* Regional market history access
* Cargo value calculation (multi-item input)
* Import run tracking

---

## Available Endpoints

| Method | Endpoint                                      | Description                       |
| :----- | :-------------------------------------------- | :-------------------------------- |
| `GET`  | `/health`                                     | Service health check              |
| `GET`  | `/db-check`                                   | Database connectivity validation  |
| `GET`  | `/items`                                      | Returns item metadata             |
| `GET`  | `/items/search?q=<query>`                     | Case-insensitive item search      |
| `GET`  | `/esi/global-prices`                          | Returns current global price data |
| `GET`  | `/market-history?type_id=<id>&region_id=<id>` | Returns historical market data    |
| `POST` | `/cargo/value`                                | Calculates total cargo value      |
| `GET`  | `/import-runs`                                | Returns import execution history  |

---

## Business Logic Layer

The API performs core data processing tasks:

* JOIN operations between item metadata and price tables to provide human-readable results
* Aggregation of multi-item cargo values
* Filtering of historical market data by region and item type

---

## Security Model

* No direct database exposure
* Controlled query surface via API endpoints
* Input validation handled by FastAPI
* Access restricted to internal network (firewall)

---

## Current Status

* Fully operational application layer
* Connected to real market data
* Multi-endpoint API structure active
* Worker integration confirmed
* Used as the primary data access layer for the upcoming web dashboard

---

## Known Limitations & Next Steps

### Limitations

* No authentication or rate limiting
* No pagination for large datasets
* Response schemas (Pydantic models) incomplete
* No caching layer (e.g. Redis)

### Next Steps

* Implement response models
* Add pagination and filtering
* Introduce caching layer
* Separate test and production endpoints
* Optimize API design for frontend consumption

