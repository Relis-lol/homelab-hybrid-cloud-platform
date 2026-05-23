# Homelab Hybrid Cloud Platform

Personal infrastructure and data platform project focused on Linux, Docker, automation, backend services, and hybrid cloud concepts.

The platform evolved from a small Ubuntu homelab into a containerized EVE Online market analysis system with automated data ingestion, API services, interactive frontend tools, and operational monitoring.

---

## Current Features

- Hardened Ubuntu Server environment
- Docker Compose multi-service stack
- PostgreSQL market database
- FastAPI backend API
- Automated ESI market imports
- Historical market data storage
- Interactive frontend dashboard
- Cargo and trade analysis tools
- Multi-chart visualization system
- Cron-based worker automation
- Discord monitoring notifications

---

## Architecture Overview

Current stack:
- Ubuntu Server
- Docker Compose
- PostgreSQL
- FastAPI
- Python worker services
- Browser-based frontend tools

The platform currently processes real EVE Online market data, stores historical pricing information, and exposes analytics tools through a modular web interface.

Current database size:
- ~16,800 item names indexed
- ~848,000 historical market records stored

---

## Project Goals

- Hybrid cloud architecture with Azure integration
- Expanded monitoring and observability
- CI/CD-driven deployment workflows
- Public deployment hardening
- Advanced market analytics features

---

## Repository Structure

```text
docs/       -> architecture and infrastructure documentation
diagrams/   -> Mermaid architecture diagrams
tabs/       -> frontend feature modules and experiments
infra/      -> infrastructure and deployment helpers
scripts/    -> automation and utility scripts
````

---

## Documentation

Detailed project documentation is available in the `/docs` directory.

Main topics:

* Linux baseline and hardening
* Docker platform architecture
* Database layer
* API layer
* Web dashboard architecture
* Observability and logging
* Azure hybrid integration
* CI/CD and automation
