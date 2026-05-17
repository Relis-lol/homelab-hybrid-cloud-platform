# Documentation

This folder contains the technical documentation for the Homelab Hybrid Cloud Platform project.

The project documents the evolution of a local Linux-based server into a containerized hybrid cloud platform focused on:

- Docker-based infrastructure
- API-driven architecture
- Automated data ingestion
- Market analytics
- Observability and monitoring
- Azure hybrid integration
- CI/CD concepts

---

# Documentation Structure

| File | Description |
|---|---|
| `01-linux-baseline.md` | Linux server setup, SSH hardening, firewall configuration |
| `02-docker-platform.md` | Docker and Docker Compose architecture |
| `03-database-layer.md` | PostgreSQL database design and persistence |
| `04-api-layer.md` | FastAPI application layer and API structure |
| `05-web-dashboard.md` | Frontend architecture and dashboard planning |
| `06-observability.md` | Logging, monitoring, worker tracking, notifications |
| `07-azure-integration.md` | Planned Azure hybrid cloud integration |
| `08-cicd-automation.md` | CI/CD and deployment automation concepts |

---

# Architecture Diagrams

Additional architecture diagrams are available in:

```text
/diagrams
```

These diagrams visualize:

- Current platform architecture
- Data flow between services
- Future hybrid cloud architecture

---

# Current Project State

The platform currently includes:

- Hardened Ubuntu server
- Docker Compose infrastructure
- PostgreSQL database
- FastAPI backend
- Worker-based EVE market imports
- Historical market data storage
- Cargo calculation tools
- Interactive market charts
- Cron-based automation
- Discord monitoring integration

The project is actively evolving toward a production-style hybrid cloud platform with monitoring, automation, and Azure integration.
