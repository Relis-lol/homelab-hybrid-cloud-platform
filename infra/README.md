# Infrastructure

Infrastructure layer for the EVE Market Platform.

Focus areas include Linux administration, containerized services, networking, security, automation, observability, and future hybrid-cloud integration.

---

# 🎯 Purpose

Provide the foundation for reliable, reproducible, and secure platform operations.

---

# 🛠️ Current Infrastructure

| Area               | Technology                            |
| ------------------ | ------------------------------------- |
| Operating System   | Ubuntu Server 24.04 LTS               |
| Container Platform | Docker Compose                        |
| Database           | PostgreSQL 16                         |
| Backend Services   | FastAPI                               |
| Automation         | Python Workers                        |
| Monitoring         | Discord-based operational reporting   |
| Security           | UFW, SSH hardening, service isolation |
| Network            | Private LAN deployment                |

---

# 🧱 Design Decisions

* Containers communicate through an internal Docker network

  * database is not exposed externally

* Infrastructure remains reproducible

  * services can be rebuilt from configuration

* Operational visibility is prioritized

  * worker reporting and runtime monitoring included

* Security-first homelab design

  * minimal attack surface and restricted access

* Hybrid-cloud architecture planned from the beginning

  * future Azure integration without redesigning the platform

---

# 🚀 Example Operations

```bash
docker compose up -d

docker compose build api --no-cache

docker compose logs --tail=120 worker

docker compose ps
```

---

# ☁️ Planned Infrastructure Expansion

* Azure networking and cloud resources
* Infrastructure as Code (IaC)
* GitHub Actions deployment pipelines
* Automated backup workflows
* Advanced observability stack
* Hybrid-cloud deployment scenarios

---

# 🔧 Future Technologies

* Terraform
* Bicep
* GitHub Actions
* Azure
* Docker Registry
* Infrastructure Validation Pipelines
