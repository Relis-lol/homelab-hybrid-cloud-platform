# Documentation

This directory contains the technical documentation for the Homelab Hybrid Cloud Platform project.

The project documents the evolution of a Linux homelab server into a containerized market data and hybrid cloud platform focused on:
- Docker-based infrastructure
- API-driven architecture
- Automated EVE market data ingestion
- Interactive analytics tools
- Monitoring and observability
- Azure hybrid integration
- CI/CD concepts and automation

---

# Documentation Structure

| File | Description |
|---|---|
| `01-linux-baseline.md` | Ubuntu server setup, SSH hardening, firewall configuration |
| `02-docker-platform.md` | Docker and Docker Compose architecture |
| `03-database-layer.md` | PostgreSQL database structure and persistence |
| `04-api-layer.md` | FastAPI backend and API design |
| `05-web-dashboard.md` | Frontend structure and dashboard features |
| `06-observability.md` | Logging, monitoring, worker tracking, notifications |
| `07-azure-integration.md` | Planned hybrid cloud integration with Azure |
| `08-cicd-automation.md` | CI/CD and deployment automation concepts |

---

# Related Directories

```text
/diagrams
/infra
/scripts
```

These directories contain:
- Mermaid architecture diagrams
- Infrastructure-related files
- Automation and helper scripts

---

# Current Platform State

Currently implemented:
- Hardened Ubuntu server
- Docker Compose infrastructure
- PostgreSQL database
- FastAPI backend API
- Worker-based EVE market imports
- Historical market data storage
- Cargo and trade analysis tools
- Interactive market charts
- Cron-based worker automation
- Discord monitoring integration

The platform is actively evolving toward a production-style hybrid cloud and analytics environment.
