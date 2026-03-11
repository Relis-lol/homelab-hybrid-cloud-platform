# 02 – Docker Platform

## Objective

Use Docker as the runtime platform for all application services.

Docker enables isolated services, reproducible deployments and a clear separation between the host system and application layer.

---

## Installation Overview

- Docker Engine installed via official repository
- Docker service enabled and running
- Docker Compose installed and operational
- Initial container tests successful

---

## Platform Role in Architecture

Docker acts as the execution layer for all services.

Ubuntu Host → Docker Engine → Compose Stack → Containers (Database / API / Future Services)

Responsibilities:

- run application services
- isolate workloads
- manage internal networking
- handle persistent storage through volumes

---

## Project Structure

Current project structure:

~/stack/
└── eve-stack/
    ├── compose.yml
    ├── api/
    │   ├── app.py
    │   ├── requirements.txt
    │   └── Dockerfile
    ├── database/
    └── frontend/

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

Validated results:

- Compose stack builds successfully
- Containers start correctly
- PostgreSQL persists data through a named volume
- API is reachable from the local network
- Internal container communication works via service names

---

## Networking Model

Docker Compose creates an internal network for the stack.

Service communication uses container names:

- postgres → database service
- api → application service

Database traffic remains internal to the Docker network.

---

## Volume Strategy

PostgreSQL uses a named Docker volume:

postgres-data


This ensures database persistence even if containers are recreated.

---

## Port Management

Currently exposed ports:

- 8000/tcp → API service (LAN access only)
- 5432/tcp → not exposed externally

The database port was intentionally removed to keep the database internal to the container network.

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
- Compose stack operational
- PostgreSQL container running
- FastAPI container running
- API reachable through port 8000
- Database accessible internally via Docker network

---

## Known Limitations

- No reverse proxy configured yet
- No monitoring stack deployed
- No environment file separation yet
- No automated container update workflow

---

## Next Steps

- Connect API service to PostgreSQL
- Move credentials into environment variables
- Introduce reverse proxy layer
- Add logging and monitoring services
