# 02 – Docker Platform

## Objective

Use Docker as the runtime platform for all application services.

The platform uses containerized services for reproducibility, isolation, and simplified deployment management.

---

## Installation Overview

- Docker Engine installed via official repository
- Docker service enabled on boot
- Docker Compose plugin installed (`docker compose`)
- Multi-container setup validated successfully

---

## Platform Role

Docker acts as the execution layer for the platform services.

```text
Ubuntu Host → Docker Engine → Compose Stack → Containers
```

### Current Service Roles

- PostgreSQL → persistent database
- FastAPI → backend API layer
- Worker → automated import pipeline
- Frontend → planned public dashboard

---

## Project Structure

```text
~/stack/
└── eve-stack/
    ├── compose.yml
    ├── .env
    ├── api/
    │   ├── app.py
    │   ├── requirements.txt
    │   └── Dockerfile
    ├── worker/
    │   ├── worker.py
    │   ├── requirements.txt
    │   └── Dockerfile
    ├── database/
    └── frontend/
```

### Structure Philosophy

- Clear separation of responsibilities
- Easier service scaling and maintenance
- Better long-term organization for multi-service infrastructure

---

## Compose Stack Design

### Long-running Services

- `postgres` → PostgreSQL 16 database container
- `api` → FastAPI backend container

### One-shot Services

- `worker` → batch-style import container

---

## Worker Execution Model

The worker is intentionally designed as a one-shot batch process instead of a continuously running background service.

### Manual Execution

```bash
docker compose run --rm worker
```

With optional enrichment:

```bash
docker compose run --rm -e ENABLE_NAME_ENRICHMENT=true worker
```

### Current Behavior

- Container starts
- Imports market data
- Writes to PostgreSQL
- Sends optional notifications
- Exits after completion

### Design Rationale

- Prevents uncontrolled loops
- Simplifies scheduling
- Easier debugging and recovery
- Better alignment with batch-processing workflows

---

## Automation Strategy

Worker execution is currently handled through cron-based scheduling outside the container stack.

### Current Automation

- Scheduled periodic imports
- Optional manual enrichment runs
- Controlled execution timing

### Benefits

- Predictable execution behavior
- Clear separation between runtime and scheduling
- Easier operational control

---

## Networking Model

Docker Compose provides internal service networking.

Containers communicate using Docker service names instead of static IP addresses.

### Internal Communication

- `api` ↔ `postgres`
- `worker` ↔ `postgres`

Database traffic remains internal to the Docker network.

---

## Storage Strategy

PostgreSQL uses a persistent named Docker volume:

```text
postgres-data
```

This preserves database data independently from container lifecycle operations.

---

## Port Management

### Exposed

- `8000/tcp` → FastAPI service (LAN only)

### Internal Only

- `5432/tcp` → PostgreSQL database

Firewall rules additionally restrict access to the local subnet.

---

## Environment & Secrets

Configuration values and secrets are handled through environment variables.

### Examples

- Database credentials
- Worker flags
- Discord webhook configuration

Stored in:

```text
.env
```

### Benefits

- Cleaner configuration management
- Separation between code and secrets
- Easier environment migration

---

## Security Considerations

- No direct public exposure
- Database isolated inside Docker network
- Firewall-restricted access
- SSH limited to local subnet
- Secrets externalized from application code

---

## Current Status

Currently operational:

- Stable Docker Compose environment
- Persistent PostgreSQL database
- FastAPI backend API
- Automated worker imports
- Cron-based scheduling
- Discord notification integration
- Internal container networking

---

## Known Limitations

- No reverse proxy yet
- No centralized monitoring stack
- No container health monitoring
- No automated deployment pipeline
- No scaling strategy implemented

---

## Next Steps

- Introduce reverse proxy layer
- Add centralized logging and monitoring
- Implement health checks
- Prepare deployment automation
- Integrate CI/CD workflows
