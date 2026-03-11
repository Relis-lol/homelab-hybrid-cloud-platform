# 04 – API Layer

## Objective

Provide a controlled application layer between the database and external consumers.

The API handles data access, request validation and structured responses.

---

## Technology Stack

- Python FastAPI
- Docker container deployment
- Uvicorn ASGI server

---

## Architecture Concept

The API runs as a container inside the Docker Compose stack.

Communication flow:

Client → API → PostgreSQL

Key characteristics:

- database access only through API
- internal container communication via Docker network
- external access limited to defined API endpoints

---

## Responsibilities

The API layer is responsible for:

- processing incoming requests
- retrieving structured data from the database
- returning JSON responses
- abstracting database logic from clients

Future responsibilities:

- market data queries
- price history retrieval
- controlled read-only endpoints

---

## Security Model

- no direct database exposure
- API acts as controlled access gateway
- input validation handled by FastAPI
- firewall restricts access to local network
- request logging planned

---

## Current Status

- FastAPI service container deployed
- Container integrated into Docker Compose stack
- Health endpoint implemented

Available endpoint:
/health

API reachable via:
http://<server-ip>:8000/health


---

## Next Steps

- implement database connection
- create initial data query endpoints
- introduce request logging
- prepare API structure for future services
