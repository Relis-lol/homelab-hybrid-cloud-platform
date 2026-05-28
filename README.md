# Homelab Hybrid Cloud Platform

Containerized EVE Online market intelligence platform focused on backend engineering, data pipelines, analytics tooling, observability, and hybrid-cloud concepts.

Built as a real-world infrastructure and automation portfolio project using Linux, Docker, PostgreSQL, FastAPI, Python workers, and modular frontend systems.

---

# 🚀 Core Features

| Area | Features |
|---|---|
| Infrastructure | Hardened Ubuntu Server, Docker Compose stack, service isolation |
| Backend | FastAPI API layer, modular worker architecture, scheduled ingestion |
| Database | PostgreSQL analytics database, historical market storage |
| Data Pipeline | Automated ESI imports, paginated sync system, snapshot aggregation |
| Analytics | Trade recommendations, ROI analysis, MAV15 liquidity scoring |
| Frontend | Interactive dashboard, multi-chart analytics, route-risk tools |
| Observability | Discord monitoring, runtime metrics, import reporting |
| Localization | Multilingual EVE item support |
| Architecture | Hybrid-cloud ready structure with Azure integration planning |

---

# 📊 Current Scale

| Metric | Value |
|---|---|
| Indexed Items | ~16,800 |
| Historical Market Records | ~848,000 |
| Trade Hubs Supported | Jita, Amarr, Dodixie, Hek, Rens |
| Data Sources | ESI Regional History + Live Market Snapshots |
| Frontend Charts | Hourly + Daily analytics modes |

---

# 🧱 Architecture

```text
Ubuntu Server
│
├── Docker Compose
│   ├── PostgreSQL
│   ├── FastAPI Backend
│   ├── Python Workers
│   └── Frontend Services
│
├── ESI Market Ingestion
├── Snapshot Aggregation
├── Trade Recommendation Engine
└── Interactive Analytics Dashboard
````

---

# ⚙️ Key Engineering Decisions

* Modular worker split instead of one monolithic ingestion script

  * easier maintenance and safer debugging

* Incremental paginated market synchronization

  * prevents ESI timeout and 504 instability

* Strict trade-hub filtering

  * removes false arbitrage from citadels and edge stations

* Historical + live snapshot combination

  * enables long-term analytics and future AI-assisted analysis

* Fee-aware trade calculations

  * realistic profitability instead of fake raw spread numbers

* Lightweight frontend architecture

  * responsive browser performance without heavy frameworks

---

# 📂 Repository Structure

```text
docs/       -> infrastructure and architecture documentation
diagrams/   -> Mermaid diagrams and schema visuals
tabs/       -> frontend feature modules and tool systems
infra/      -> deployment and infrastructure helpers
scripts/    -> automation and utility scripts
assets/     -> screenshots and visual assets
```

---

# 📚 Documentation

| File                      | Topic                        |
| ------------------------- | ---------------------------- |
| `01-linux-baseline.md`    | Ubuntu setup & hardening     |
| `02-docker-platform.md`   | Container architecture       |
| `03-database-layer.md`    | PostgreSQL structure         |
| `04-api-layer.md`         | FastAPI backend              |
| `05-web-dashboard.md`     | Frontend systems             |
| `06-observability.md`     | Monitoring & logging         |
| `07-azure-integration.md` | Hybrid-cloud planning        |
| `08-cicd-automation.md`   | CI/CD & deployment workflows |

---

# 🖼️ Platform Preview

| Dashboard              | Charts               | Trade Tools      |
| ---------------------- | -------------------- | ---------------- |
| `market-dashboard.png` | `market-charts1.png` | `trade-calc.png` |
| `route-risk.png`       | `market-charts2.png` | `wh-mapper.png`  |

---

# 🔮 Planned Expansion

* AI-assisted market news analysis
* Anomaly and event detection
* Advanced logistics route intelligence
* Public deployment hardening
* Azure-integrated hybrid infrastructure
* CI/CD-driven automated deployments
* Expanded observability stack

---

# 🛠️ Stack

```text
Ubuntu Server
Docker Compose
PostgreSQL
FastAPI
Python
Chart.js
JavaScript
Discord Webhooks
Mermaid
```
