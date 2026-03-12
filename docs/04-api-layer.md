# 04 – API Layer

## Objective

Provide a controlled application layer between the database and external consumers.

The API handles data access, request validation, and structured responses while abstracting direct database interaction from clients.

---

## Technology Stack

- Python FastAPI
- Docker container deployment
- Uvicorn ASGI server
- PostgreSQL access via `psycopg`

---

## Architecture Concept

The API runs as a container inside the Docker Compose stack.

### Communication Flow

Client → API → PostgreSQL

### Key Characteristics

- Database access occurs only through the API
- Internal service communication uses Docker networking
- External access limited to defined API endpoints
- JSON used as the response format

---

## Responsibilities

The API layer is responsible for:

- Processing incoming requests
- Validating request parameters
- Retrieving structured data from the database
- Returning JSON responses
- Abstracting database logic from clients

### Current Implemented Responsibilities

- Health verification
- Database connectivity check
- Item retrieval
- Market price retrieval
- Item search functionality
- Import run history retrieval
- Test data seeding for validation

### Future Responsibilities

- Market data queries by item and region
- Historical filtering
- Read-only dashboard support
- Structured response models
- Authentication or access control if public exposure is introduced later

---

## Security Model

- No direct database exposure
- API acts as the controlled access gateway
- Input validation handled by FastAPI
- Firewall restricts access to the internal network
- Database credentials injected through container environment variables
- Request logging planned but not yet implemented

---

## Current Status

- FastAPI service container deployed
- Container integrated into Docker Compose stack
- Database connection established
- Internal Docker networking validated
- API reachable from the local network
- Read and write validation endpoints operational

---

## Available Endpoints

### `GET /health`

Basic service health check.

**Purpose**

- Confirm that the API container is running
- Verify that the service is reachable

---

### `GET /db-check`

Database connectivity validation endpoint.

**Purpose**

- Confirm API-to-database communication
- Verify active database and user context

---

### `POST /seed-test-data`

Inserts controlled test records into the database.

**Purpose**

- Validate write access
- Seed sample item and market data for testing

---

### `GET /items`

Returns stored item reference records.

**Purpose**

- Verify item retrieval logic
- Expose current contents of the `item_types` table

---

### `GET /prices`

Returns recent market price records.

**Purpose**

- Verify historical data retrieval
- Expose current contents of the `market_prices` table

---

### `GET /items/search?q=...`

Performs case-insensitive search against item names.

**Purpose**

- Validate query parameter handling
- Support item lookup by partial name

---

### `GET /import-runs`

Returns recent worker import executions.

**Purpose**

- Expose batch import history
- Validate worker → database → API data flow

---

## Validation Results

The API layer has already been validated through live tests:

- `/db-check` confirmed successful PostgreSQL connectivity
- `/seed-test-data` inserted test records successfully
- `/items` returned stored item metadata
- `/prices` returned stored market history data
- `/items/search` returned filtered results correctly
- `/import-runs` returned worker execution history correctly

These results confirm that the API is already functioning as a real application layer on top of PostgreSQL.

---

## Access Pattern

Example endpoint access:

`http://<server-ip>:8000/health`

Equivalent endpoint patterns apply to other routes, for example:

- `http://<server-ip>:8000/db-check`
- `http://<server-ip>:8000/items`
- `http://<server-ip>:8000/prices`
- `http://<server-ip>:8000/items/search?q=tri`
- `http://<server-ip>:8000/import-runs`

---

## Known Limitations

- No response schemas defined yet
- No pagination implemented
- No authentication layer
- No request logging implemented
- No rate limiting
- No public-ready API documentation strategy yet
- Current write endpoint exists only for controlled testing

---

## Next Steps

- Add structured response models
- Introduce filtering for market queries
- Separate test-only endpoints from production-facing endpoints
- Prepare API design for frontend consumption
- Integrate real EVE market import output from worker processes
