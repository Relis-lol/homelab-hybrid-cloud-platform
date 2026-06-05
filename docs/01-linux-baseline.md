
# 01 – Linux Baseline

Linux infrastructure foundation for the EVE Trade Intelligence Platform.

The system hosts the production environment, databases, backend services, automation workflows, and public web platform.

---

# 🎯 Purpose

Provide a secure, lightweight, and reproducible Linux environment for self-hosted infrastructure workloads.

---

# 🛠️ Hardware

| Component      | Specification                 |
| -------------- | ----------------------------- |
| System         | NiPoGi 4K Mini PC             |
| CPU            | AMD Ryzen 3 4300U (4C / 4T)   |
| Memory         | 16 GB DDR4                    |
| Storage        | 512 GB SSD                    |
| Backup Storage | External SSD Backup Drive     |
| Monitoring     | ESP32 CYD 2.8" Status Display |

---

# 📟 Monitoring Display

The ESP32 CYD provides lightweight infrastructure monitoring with a 30-second refresh interval.

Displayed metrics:

* API status
* Database status
* Worker status
* CPU utilization
* RAM utilization
* SSD usage
* Network traffic
* System temperature
* Last synchronization time

---

# 🖥️ Operating System

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

  * reduced resource usage and attack surface

* Ubuntu Server LTS

  * stable platform with long-term support

* Container-first architecture

  * services remain isolated and reproducible

* Self-hosted infrastructure

  * full control over deployment and operations

* Local backup strategy

  * supports recovery and rollback workflows

---

# 🌐 Network Configuration

| Area          | Configuration           |
| ------------- | ----------------------- |
| Connectivity  | Wired LAN               |
| Addressing    | DHCP Reservation        |
| Remote Access | SSH Key Authentication  |
| Public Access | Web Platform Deployment |
| Domain        | eve-tradelooper.com     |

---

# 🌍 Domain & DNS Automation

Cloudflare Dynamic DNS automation maintains public availability of the platform.

Features:

* Automatic public IP updates
* Cloudflare API integration
* Restricted DNS-scoped API tokens
* Reduced operational maintenance

This allows the platform to remain reachable even when the ISP-assigned public IP changes.

---

# 🔐 Security Baseline

### SSH

* ED25519 key authentication
* Password login disabled
* Root login disabled
* Restricted administrative access

### Firewall

* UFW enabled
* Default deny incoming
* Service-specific access rules
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

| Service         | Purpose                    |
| --------------- | -------------------------- |
| PostgreSQL      | Analytics database         |
| FastAPI         | Backend API                |
| Worker Services | Automated market ingestion |
| Frontend        | Public dashboard delivery  |

---

# 🚀 Current Capabilities

* Containerized application stack
* Automated worker execution
* Historical market analytics
* Public web deployment
* Local backup workflows
* Real-time monitoring display
* Cloudflare DNS automation
* Production platform hosting

---

# 📈 Current Status

**Live Production Environment**

Hosts:

* Market analytics
* Historical data storage
* Trade intelligence systems
* Dashboard services
* Monitoring workflows

Platform URL:

https://eve-tradelooper.com/
