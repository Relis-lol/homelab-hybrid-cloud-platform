# 01 – Linux Baseline

Linux infrastructure foundation for the EVE Market Platform.

This system serves as the primary host for containers, databases, backend services, automation workflows, and future hybrid-cloud integrations.

---

# 🎯 Purpose

Provide a secure, lightweight, and reproducible Linux platform for self-hosted infrastructure workloads.

---

# 🛠️ Hardware

| Component      | Specification                    |
| -------------- | -------------------------------- |
| System         | NiPoGi 4K Mini PC                |
| CPU            | AMD Ryzen 3 4300U (4C / 4T)      |
| Memory         | 16 GB DDR4                       |
| Storage        | 512 GB SSD                       |
| Backup Storage | External SSD-based backup device |

---

# 🛠️ Operating System

| Component     | Configuration           |
| ------------- | ----------------------- |
| OS            | Ubuntu Server 24.04 LTS |
| GUI           | None                    |
| Storage       | LVM                     |
| Remote Access | OpenSSH                 |
| Boot Mode     | Headless                |

---

# 🧱 Key Design Decisions

* Headless Linux deployment

  * reduces resource usage and attack surface

* Ubuntu Server LTS

  * stable platform with long-term support

* Container-first architecture

  * services remain isolated and reproducible

* LAN-only deployment

  * simplifies operations and minimizes exposure

* Backup strategy included from the beginning

  * supports recovery and rollback workflows

---

# 🌐 Network Architecture

| Area            | Configuration      |
| --------------- | ------------------ |
| Connectivity    | Wired LAN          |
| Addressing      | DHCP reservation   |
| Exposure        | No public services |
| Port Forwarding | Disabled           |
| Access Scope    | Local network only |

---

# 🔐 Security Baseline

### SSH

* ED25519 key authentication
* Password login disabled
* Root login disabled
* Restricted network access

### Firewall

* UFW enabled
* Default deny incoming
* LAN-restricted service access
* Logging enabled

### Intrusion Protection

* Fail2ban enabled
* SSH protection active

---

# 🐳 Container Platform

### Runtime

* Docker Engine
* Docker Compose

### Active Services

| Service         | Purpose                  |
| --------------- | ------------------------ |
| PostgreSQL      | Data storage             |
| FastAPI         | Backend API              |
| Worker Services | Automated data ingestion |
| Frontend        | Dashboard delivery       |

---

# 🚀 Current Capabilities

* Headless Linux server
* Hardened remote access
* Containerized application stack
* Automated worker execution
* Local backup workflows
* LAN-only API access

---

# ⚠️ Current Limitations

* No reverse proxy
* No public HTTPS
* No centralized observability stack
* No CI/CD deployment pipeline
* No Azure integration yet

---

# 🔮 Planned Expansion

* Advanced monitoring and logging
* Automated backup management
* Azure hybrid-cloud integration
* Infrastructure as Code
* CI/CD deployment workflows
* Public deployment hardening
