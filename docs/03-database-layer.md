# 03 – Database Layer

## Objective

Introduce a structured database backend to support application logic and data persistence.

---

## Planned Stack

- PostgreSQL (Docker container)
- Dedicated Docker volume for persistent storage
- Internal network exposure only

---

## Architecture Concept

- Database runs inside isolated Docker network
- No direct public exposure
- API layer acts as single access point

---

## Security Considerations

- Strong password enforcement
- Environment variables via `.env`
- No hardcoded credentials
- No external port exposure

---

## Data Scope

Planned data usage:

- EVE Online market history
- Structured pricing data
- Timestamped historical records

---

## Current Status

Not yet deployed.

---

## Next Steps

- Deploy PostgreSQL container
- Create initial schema
- Validate persistence
- Test internal connectivity from API container
