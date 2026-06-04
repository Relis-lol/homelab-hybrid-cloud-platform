# 02 – Docker Platform

Container platform powering the EVE Trade Intelligence Platform.

Docker Compose is used to provide service isolation, reproducible deployments, and simplified platform operations.

---

# 🎯 Purpose

Run the complete application stack through containerized services with consistent deployment and recovery workflows.

---

# 🛠️ Platform Overview

```text
Ubuntu Host
      ↓
Docker Engine
      ↓
Docker Compose
      ↓
Application Services
```

### Active Services

| Service    | Purpose                   |
| ---------- | ------------------------- |
| PostgreSQL | Analytics database        |
| FastAPI    | Backend API               |
| Worker     | Market ingestion pipeline |
| Frontend   | Public web platform       |

---

# 📂 Project Structure

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

---

# 🧱 Key Design Decisions

* Containerized service architecture

  * isolates application components

* Docker Compose orchestration

  * simplified deployment and maintenance

* Persistent database storage

  * data survives container recreation

* Internal service networking

  * database remains inaccessible from public endpoints

* Environment-based configuration

  * secrets remain separated from application code

---

# 🔄 Worker Architecture

The ingestion worker operates as a one-shot batch process instead of a permanently running service.

### Manual Execution

```bash
docker compose run --rm worker
```

### Optional Enrichment Mode

```bash
docker compose run --rm -e ENABLE_NAME_ENRICHMENT=true worker
```

### Worker Responsibilities

* Market data ingestion
* Snapshot generation
* Historical data updates
* Database writes
* Discord notifications
* Import reporting

---

# ⏰ Automation

Worker execution is scheduled externally through cron.

Current automation includes:

* Scheduled market imports
* Snapshot generation
* Controlled execution timing
* Manual execution support

---

# 🌐 Internal Networking

Docker Compose provides isolated networking between services.

### Service Communication

```text
Frontend → API
API → PostgreSQL
Worker → PostgreSQL
```

Database traffic remains internal to the Docker network.

---

# 💾 Persistent Storage

PostgreSQL data is stored in a dedicated Docker volume:

```text
postgres-data
```

This allows containers to be rebuilt without affecting stored analytics data.

---

# 🔒 Environment & Security

Configuration is managed through:

```text
.env
```

Examples include:

* Database credentials
* Worker configuration
* Discord webhook settings

### Security Principles

* No public database exposure
* Internal Docker networking
* Environment-based secrets
* Service isolation
* Firewall-protected host

---

# 📈 Current Status

**Live Production Environment**

* Stable Docker Compose stack
* Persistent PostgreSQL database
* FastAPI backend services
* Automated worker pipeline
* Scheduled ingestion workflows
* Public frontend deployment
* Internal service networking

Platform URL:

https://eve-tradelooper.com/
