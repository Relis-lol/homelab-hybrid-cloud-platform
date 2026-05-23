# Architecture Diagrams

This directory contains Mermaid graph definitions used to visualize the platform architecture and data flow.

The files are intentionally lightweight and focused on diagram rendering rather than long-form documentation.

---

## Available Diagrams

### current-architecture.md
Current homelab platform structure:
- Docker services
- API layer
- Worker pipeline
- PostgreSQL database
- Security components
- Planned Azure integration

---

### data-flow.md
Market data processing flow:
- EVE ESI ingestion
- Worker processing
- Database persistence
- API access
- Frontend visualization

---

### future-hybrid-architecture.md
Planned future deployment and hybrid cloud direction:
- Azure services
- Backup workflows
- Monitoring concepts
- Public deployment structure
- Hybrid infrastructure model

---

## Notes

- All files contain Mermaid graph definitions only
- Designed for GitHub-native rendering
- Lightweight and easy to maintain
- Used as visual support for the documentation in `/docs`
