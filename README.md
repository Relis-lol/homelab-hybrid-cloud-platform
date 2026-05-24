# Homelab Hybrid Cloud Platform

Personal infrastructure and data platform project focused on Linux, Docker, automation, backend services, and hybrid cloud concepts.

The platform evolved from a small Ubuntu homelab into a containerized EVE Online market analysis system with automated data ingestion, historical market tracking, API services, interactive frontend tools, and operational monitoring.

---

## Current Features

- Hardened Ubuntu Server environment
- Docker Compose multi-service stack
- PostgreSQL market database
- FastAPI backend API
- Automated ESI market imports
- Historical regional market tracking
- Multilingual EVE item support
- Interactive frontend dashboard
- Cargo, trade, and route analysis tools
- Multi-chart visualization system
- Cron-based worker automation
- Discord monitoring notifications
- Basic operational observability

---

## Architecture Overview

Current stack:

- Ubuntu Server
- Docker Compose
- PostgreSQL
- FastAPI
- Python worker services
- Browser-based frontend tools

The platform processes real EVE Online market data, stores historical pricing information across multiple regions, and exposes analytics tools through a modular web interface.

Current database scale:

- ~16,800 item names indexed
- ~848,000 historical market records stored
- Official multilingual item translations supported

---

## Project Goals

- Hybrid cloud architecture with Azure integration
- Expanded monitoring and observability
- CI/CD-driven deployment workflows
- Public deployment hardening
- Advanced market and route analytics
- AI-assisted analysis experiments

---

## Repository Structure

```text
docs/       -> architecture and infrastructure documentation
diagrams/   -> Mermaid architecture diagrams
tabs/       -> frontend feature modules and experiments
infra/      -> infrastructure and deployment helpers
scripts/    -> automation and utility scripts
assets/     -> screenshots and visual assets
```

---

## Documentation

Detailed project documentation is available in the `/docs` directory.

Main topics:

- Linux baseline and hardening
- Docker platform architecture
- Database layer
- API layer
- Web dashboard architecture
- Observability and logging
- Azure hybrid integration
- CI/CD and automation
