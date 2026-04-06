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
    ├── .env
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
---

### Rationale

* Clear separation of service responsibilities
* Easier future expansion
* Better alignment with multi-service architecture
* Maintainable structure for scaling services

---

## Compose Stack Design

### Long-running services

* `postgres` → PostgreSQL 16 container (persistent database)
* `api` → FastAPI container (application layer)

### One-shot services

* `worker` → batch-style import container

---

## Worker Execution Model

The worker is designed as a **one-shot batch job**, not a continuously running service.

### Execution Methods

Manual execution:

```
docker compose run --rm worker
```

With enrichment enabled:

```
docker compose run --rm -e ENABLE_NAME_ENRICHMENT=true worker
```

### Behavior

* Container starts → executes import → exits
* No restart policy (`restart: "no"`)
* Writes data to PostgreSQL
* Logs execution results
* Sends optional Discord notifications

### Rationale

* Prevents uncontrolled background loops
* Allows explicit scheduling and control
* Aligns with real-world batch processing patterns

---

## Automation Strategy

Worker execution is automated using system-level scheduling (cron).

### Current Setup

* Periodic execution (e.g. hourly)
* Optional enrichment runs on demand
* Centralized control outside Docker

### Benefits

* Clear separation between runtime and scheduling
* Predictable execution behavior
* Easy debugging and manual override

---

## Networking Model

Docker Compose creates an internal network for the stack.

Service-to-service communication uses Docker's internal DNS.

Example:

* `postgres` → database service
* `api` → application service
* `worker` → import service

Containers communicate using service names instead of IP addresses.

Database traffic remains internal to the Docker network.

---

## Volume Strategy

PostgreSQL uses a named Docker volume:

```
postgres-data
```

This ensures database persistence even if containers are recreated.

---

## Port Management

Currently exposed ports:

* `8000/tcp` → API service (LAN access only)

Not exposed:

* `5432/tcp` → PostgreSQL (internal only)

Firewall rules restrict API access to the local subnet.

---

## Environment & Secrets

Environment variables are used for configuration and secrets.

### Examples

* Database credentials
* Worker configuration flags
* Discord webhook URL

Stored in:

```
.env
```

### Benefits

* Separation of config and code
* Safer secret handling
* Easier environment switching

---

## Security Considerations

* No direct public exposure
* Database hidden behind container network
* Firewall restricts access to LAN
* SSH restricted to internal subnet
* Secrets externalized via `.env`

---

## Current Status

* Docker operational
* Compose stack stable
* PostgreSQL running with persistent storage
* API container serving requests
* Worker executing real EVE data imports
* One-shot worker model validated
* Cron-based automation in place
* Discord notifications integrated
* Internal networking fully functional

---

## Known Limitations

* No reverse proxy configured yet
* No centralized logging stack
* No container health monitoring
* No auto-redeploy or update strategy
* No horizontal scaling

---

## Next Steps

* Introduce reverse proxy (Nginx / Traefik)
* Add centralized logging and monitoring
* Implement health checks and alerts
* Prepare container update strategy
* Integrate with CI/CD pipeline


