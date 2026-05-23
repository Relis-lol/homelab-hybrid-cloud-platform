# 02 – Docker Platform

## Objective

Docker is used as the runtime platform for all application services.

The platform uses containerized services for isolation, reproducibility, and simplified deployment management.

---

## Platform Overview

```text
Ubuntu Host → Docker Engine → Compose Stack → Containers
```

### Current Services

- PostgreSQL → persistent database
- FastAPI → backend API
- Worker → market import pipeline
- Frontend → planned dashboard

---

## Project Structure

```text
~/stack/
└── eve-stack/
    ├── compose.yml
    ├── .env
    ├── api/
    ├── worker/
    ├── database/
    └── frontend/
```

The structure separates services cleanly and keeps the platform easier to maintain as new components are added.

---

## Worker Design

The worker runs as a one-shot batch container instead of a permanent background service.

### Manual Execution

```bash
docker compose run --rm worker
```

Optional enrichment mode:

```bash
docker compose run --rm -e ENABLE_NAME_ENRICHMENT=true worker
```

### Current Behavior

- Imports market data
- Writes data to PostgreSQL
- Sends optional Discord notifications
- Exits after completion

### Why This Model

- Prevents uncontrolled loops
- Easier debugging and recovery
- Better control over execution timing
- Closer to real-world batch processing

---

## Automation

Worker execution is currently handled through cron scheduling outside Docker.

Current automation includes:

- Scheduled imports
- Manual enrichment runs
- Controlled execution timing

---

## Networking

Docker Compose provides internal networking between services.

### Internal Communication

- `api` ↔ `postgres`
- `worker` ↔ `postgres`

Database traffic remains internal to the Docker network and is not exposed publicly.

---

## Storage

PostgreSQL uses a persistent Docker volume:

```text
postgres-data
```

This keeps database data independent from container recreation.

---

## Environment & Security

Configuration and secrets are handled through environment variables stored in:

```text
.env
```

Examples include:

- Database credentials
- Worker flags
- Discord webhook configuration

### Security Model

- No direct public database exposure
- Database isolated inside Docker network
- Firewall restricts LAN access
- SSH limited to local subnet
- Secrets separated from application code

---

## Current Status

Operational components:

- Stable Docker Compose stack
- Persistent PostgreSQL database
- FastAPI backend
- Automated worker imports
- Cron-based scheduling
- Discord notifications
- Internal container networking

---

## Known Limitations

- No reverse proxy yet
- No centralized monitoring stack
- No container health monitoring
- No deployment automation yet

---

## Next Steps

- Add reverse proxy layer
- Introduce centralized logging
- Implement health checks
- Prepare CI/CD integration
