# 01 – Linux Baseline Setup

## Hardware

**Model:** NiPoGi 4K Mini PC  
**CPU:** AMD Ryzen 3 4300U (4C / 4T)  
**RAM:** 16GB DDR4  
**Storage:** 512GB SSD  

The system originally shipped with Windows 11 Pro and was converted into a dedicated Linux server platform.

### Hardware Rationale

- Low power consumption
- Suitable for 24/7 operation
- Enough performance for Docker workloads
- Upgradeable RAM and storage
- Cost-efficient homelab foundation

---

## Additional Hardware

### Backup Storage

- External SSD-based backup solution
- SanDisk SATA SSD in USB enclosure
- Dedicated for local backup and recovery workflows

### Physical Monitoring Screen (Experimental)

An older Android smartphone is currently being repurposed into a lightweight physical status display for:
- system monitoring
- worker status visibility
- future dashboard integration

This is intended as a low-cost homelab monitoring experiment.

---

## Operating System

**Ubuntu Server 24.04 LTS**

### Installation Decisions

- LVM enabled
- No GUI installed
- OpenSSH installed during setup
- Minimal package footprint
- No disk encryption

### Why Ubuntu Server

- Stable long-term support platform
- Strong Docker ecosystem compatibility
- Large community and documentation base
- Commonly used in production environments

---

## Network Configuration

- Wired LAN connection
- Router-managed DHCP reservation
- Internal IP assignment
- No public port forwarding
- No public services exposed

### Network Philosophy

The server is intentionally kept LAN-only during the current project stage to reduce attack surface and simplify infrastructure management.

---

## Access & Security

### SSH

- ED25519 key authentication
- Password login disabled
- Root login disabled
- Subnet-restricted SSH access

### Firewall (UFW)

- Enabled with deny-incoming policy
- SSH restricted to local subnet
- API port (`8000/tcp`) restricted to LAN access
- Logging enabled

### Fail2ban

- Installed and active
- SSH protection enabled

---

## Container Runtime

### Docker

- Docker Engine installed and operational
- Service enabled on boot

### Docker Compose

- Compose plugin installed (`docker compose`)
- Multi-service stack validated successfully

### Current Services

- PostgreSQL container
- FastAPI container
- Worker container

---

## Current System State

Currently operational:

- Headless Linux server
- Hardened SSH configuration
- Firewall and Fail2ban protection
- Docker Compose environment
- PostgreSQL database
- FastAPI backend
- Worker-based import pipeline
- LAN-only API access

---

## Known Limitations

- No reverse proxy yet
- No public HTTPS setup
- No centralized monitoring stack
- No CI/CD pipeline
- No Azure integration yet

---

## Next Steps

- Expand frontend/dashboard layer
- Improve monitoring and logging
- Extend automated import workflows
- Integrate additional analytics features
- Prepare hybrid cloud integration
