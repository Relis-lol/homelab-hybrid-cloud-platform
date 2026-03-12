# 02 – Docker Platform

## Objective

Use Docker as the runtime platform for all application services.

Docker enables isolated services, reproducible deployments, and a clear separation between the host system and the application layer.

---

## Installation Overview

- Docker Engine installed via official Docker repository
- Docker service enabled and running
- Docker Compose plugin installed (`docker compose`)
- Initial container tests successful

---

## Platform Role in Architecture

Docker acts as the execution layer for all services.

**Ubuntu Host → Docker Engine → Compose Stack → Containers (Database / API / Worker / Future Services)**

### Responsibilities

- Run application services
- Isolate workloads
- Manage internal container networking
- Handle persistent storage through volumes

---

## Project Structure

Current project structure:

```text
~/stack/
└── eve-stack/
    ├── compose.yml
    ├── api/
    │   ├── app.py
    │   ├── requirements.txt
    │   └── Dockerfile
    ├── worker/
    │   ├── worker.py
    │   ├── requirements.txt
    │   └── Dockerfile
    ├── database/      # planned for schema / migrations
    └── frontend/      # planned for future dashboard
```

### Rationale

- Clear separation of service responsibilities
- Easier future expansion
- Better alignment with multi-service architecture
- More maintainable than a single flat project folder

---

## Compose Stack Status

Active services:

- postgres → PostgreSQL 16 container
- api → FastAPI container
- worker → background import container

Validated results:

- Compose stack builds successfully
- Containers start correctly
- PostgreSQL persists data through a named volume
- API is reachable from the local network
- Internal container communication works via service names
- Worker can execute write operations against PostgreSQL
- Worker lifecycle behaves as expected for batch-style execution

---

## Networking Model

Docker Compose creates an internal network for the stack.

Service-to-service communication uses Docker's internal DNS.

Example:
- postgres → database service
- api → application service
- worker → import service
Containers communicate using these service names instead of IP addresses.

Database traffic remains internal to the Docker network.

---

## Volume Strategy

PostgreSQL uses a named Docker volume:

```text
postgres-data
```

This ensures database persistence even if containers are recreated.
The volume is managed by Docker and stored on the host filesystem.

---

## Port Management

Currently exposed ports:

- 8000/tcp → API service (LAN access only)

Not exposed:

- 5432/tcp → PostgreSQL (internal container access only)

The database port was intentionally removed from host exposure to keep the database internal to the container network.

Firewall rules restrict API access to the local subnet.

---

## Security Considerations

- No direct public exposure
- Database hidden behind container network
- Firewall controls host-level access
- SSH restricted to internal subnet
- Environment variable separation planned for later stages

---

## Current Status

- Docker operational
- Docker Compose stack operational
- PostgreSQL container running
- FastAPI container running
- Worker container validated
- API reachable through port 8000
- Database accessible internally via Docker network
- Batch import execution confirmed through worker logs

---

## Known Limitations

- No reverse proxy configured yet
- No monitoring stack deployed
- No .env separation yet
- No automated container update workflow
- Worker not yet scheduled for recurring imports
- External data source integration not yet implemented


---

## Next Steps

- Move credentials into environment variables or .env handling
- Introduce reverse proxy layer
- Add logging and monitoring services
- Convert the worker from test execution to real EVE market import logic
- Prepare a scheduled or triggered import execution model
