# Homelab Hybrid Cloud Platform

This project documents the step-by-step evolution of a private Linux server into a production-style hybrid cloud platform.

The platform started as a Linux homelab environment and evolved into a containerized data platform focused on automated EVE Online market data ingestion, API-driven access, and interactive frontend analysis tools.

Current platform capabilities:
- Hardened Ubuntu Server environment
- Docker-based multi-service architecture
- PostgreSQL database with persistent storage
- FastAPI backend API
- Automated worker-based ESI import pipeline
- Historical market data storage
- Cargo and trade analysis tools
- Interactive frontend charts
- Cron-based worker automation
- Discord-based monitoring notifications
- Internal network security model

---

## Goal

Transform the system into a fully featured hybrid cloud platform including:
- Real-time and historical EVE market analytics
- Interactive browser-based analysis tools
- Observability and monitoring stack
- Azure hybrid integration
- CI/CD-driven deployment workflows
- Architecture and infrastructure documentation
- Modular expansion for future analytics features

---

# Roadmap

## Phase 1 – Linux Baseline (Completed)
- Ubuntu Server installation
- SSH hardening
- UFW firewall configuration
- Fail2ban protection
- Internal network security model

---

## Phase 2 – Core Services (Completed)
- PostgreSQL database layer
- FastAPI application layer
- Docker Compose architecture
- Worker-based import pipeline
- Real ESI integration
- Historical data persistence

---

## Phase 3 – Public Web Dashboard (Major Progress)
Implemented:
- Cargo value calculator
- Trade helper integration
- Interactive historical price charts
- Multi-tab frontend system
- Dynamic chart tabs
- Responsive dark UI
- Item search integration
- Clickable chart interactions
- Historical price visualization
- Statistics cards and change tracking

Planned:
- Regional market analysis
- Buy/Sell pressure visualization
- Volatility indicators
- Moving averages
- Advanced analytics

---

## Phase 4 – Observability (Started)
Implemented:
- Worker execution tracking
- Cron-based automation
- Discord worker notifications
- Docker log visibility
- Import run monitoring

Planned:
- Structured logging
- Metrics dashboard
- Container health monitoring
- Resource usage tracking

---

## Phase 5 – Azure Hybrid Integration (Planned)
Planned integration areas:
- Azure Blob Storage backups
- Hybrid storage architecture
- Cloud-assisted monitoring
- Optional Azure-hosted frontend components
- Secure hybrid connectivity model

---

## Phase 6 – CI/CD & Automation (Started)
Implemented:
- Automated cron execution
- Controlled worker lifecycle
- Reproducible Docker builds

Planned:
- GitHub Actions workflows
- Automated validation pipelines
- Deployment automation
- Infrastructure verification

---

# Current Status

The platform has moved beyond a basic homelab setup and now operates as a functional multi-service data platform.

Currently operational:
- Docker Compose stack with PostgreSQL, API, and worker services
- Real EVE Online ESI market data ingestion
- Historical market data persistence
- Automated scheduled imports
- Stable worker execution pipeline
- Item metadata enrichment system
- Interactive frontend dashboard
- Cargo value calculation system
- Trade helper utilities
- Multi-chart visualization system
- Discord monitoring notifications

Current database scale:
- ~16,800 item names indexed
- ~848,000 historical market price records stored

The current architecture already demonstrates:
- Containerized infrastructure
- Automated data ingestion
- Persistent structured storage
- API-driven backend design
- Interactive frontend visualization
- Monitoring and operational thinking
- Modular system architecture

The next major focus areas are:
- Expanded analytics
- Azure hybrid integration
- Improved observability
- CI/CD workflows
- Public deployment hardening
