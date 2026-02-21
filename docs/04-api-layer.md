# 04 – API Layer

## Objective

Create a controlled application layer between frontend and database.

---

## Planned Architecture

- Backend service (Python FastAPI or Node.js)
- Containerized deployment
- Internal communication with database
- Reverse proxy for routing

---

## Responsibilities

- Handle data queries
- Provide structured JSON responses
- Abstract database logic
- Enforce read-only public access

---

## Security Model

- No direct DB exposure
- Input validation
- Rate limiting (planned)
- Log request metadata

---

## Current Status

Concept defined. No deployment yet.

---

## Next Steps

- Choose backend framework
- Define initial endpoints
- Connect to PostgreSQL container
- Implement basic test endpoint
