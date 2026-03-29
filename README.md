# Homelab Hybrid Cloud Platform

This project documents the step-by-step evolution of a private Linux server into a production-style hybrid cloud platform.

Current baseline:
- Ubuntu Server hardened and secured
- Docker-based multi-service platform
- PostgreSQL database with persistent storage
- FastAPI application layer
- Worker-based data ingestion pipeline
- Internal network-only exposure

Goal:
Transform this system into a fully featured hybrid cloud platform including:
- Real-time and historical market data ingestion (EVE Online ESI)
- API-driven data access layer
- Public web dashboard for analytics and visualization
- Observability and logging stack
- Azure hybrid integration
- CI/CD-driven deployment workflows
- Full architecture and decision documentation

---

## Roadmap

### Phase 1 – Linux Baseline (Completed)
- OS installation
- SSH hardening
- Firewall configuration

### Phase 2 – Core Services (Completed)
- PostgreSQL database layer
- FastAPI application layer
- Docker-based service architecture
- Worker-based import pipeline

### Phase 3 – Public Web Dashboard (In Progress)
- Market data integration
- Cargo value calculation
- Graph-based visualization

### Phase 4 – Observability
- Access logs
- Performance monitoring
- Resource tracking

### Phase 5 – Azure Hybrid Integration
- Azure resource integration
- Cloud storage / services
- Secure connection model

### Phase 6 – CI/CD & Automation
- GitHub Actions
- Deployment workflows
- Infrastructure validation

---

## Current Status

Production-style backend operational.

- Docker Compose stack running (Postgres, API, Worker)
- Database populated with real EVE market data
- API provides structured data access
- Worker performs external data ingestion
- Internal architecture validated end-to-end

Frontend, observability, and cloud integration are the next major steps.
## Current Status

Project initialized.
Linux server operational.
Documentation in progress.
