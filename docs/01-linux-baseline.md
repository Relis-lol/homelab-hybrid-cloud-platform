# 01 – Linux Baseline Setup

## Hardware

**Model:** NiPoGi 4K Mini PC  
**CPU:** AMD Ryzen 3 4300U (4 cores / 4 threads)  
**RAM:** 16GB DDR4  
**Storage:** 512GB SSD  
**Original OS:** Windows 11 Pro (replaced with Linux for server usage)

### Hardware Decision Rationale

- Low power consumption (always-on capable)
- Sufficient performance for containerized workloads
- Upgradeable RAM and storage
- Cost-efficient homelab foundation
- Suitable for Docker-based services

---

## Operating System

**Ubuntu Server 24.04 LTS**

### Installation Decisions

- Full disk usage with LVM
- No disk encryption (LUKS disabled)
- OpenSSH installed during setup
- Minimal package footprint
- No GUI environment

### Why Ubuntu Server

- Long-Term Support with 5 years of security updates
- Stable and widely adopted in production environments
- Strong Docker and cloud ecosystem compatibility
- Large documentation base and community support

---

## Network Configuration

- Wired LAN connection only
- DHCP assigned IP: `192.168.178.47`
- Router-level DHCP reservation configured
- No public ports exposed
- No port forwarding configured

### Rationale

- LAN-only exposure reduces attack surface
- DHCP reservation ensures stable addressing without OS-level static configuration
- Server remains private within the internal network

---

## Access and Security Model

### SSH Configuration

- ED25519 key pair generated on the client machine
- Public key added to `~/.ssh/authorized_keys`
- Key-based authentication verified
- `PasswordAuthentication` disabled
- `PermitRootLogin` disabled
- `PubkeyAuthentication` enforced

### Firewall (UFW)

- UFW enabled
- Default policy: deny incoming / allow outgoing
- SSH (`22/tcp`) allowed **only from `192.168.178.0/24`**
- API port (`8000/tcp`) allowed **only from `192.168.178.0/24`**
- Logging enabled at low level

#### Security Adjustment

The default OpenSSH profile rule was removed and replaced with a subnet-restricted SSH rule.

**Impact**

- SSH access restricted to the internal network
- Reduced attack surface
- No external SSH exposure through current network configuration

### Fail2ban

- Installed and enabled
- SSH jail active with default configuration

**Objective**

Mitigate brute-force attempts even within internal network environments.

---

## System Hardening

- System fully updated using `apt update && apt upgrade`
- Headless server operation
- No unnecessary packages installed
- SSH key-based access enforced

### Security Philosophy

- Principle of minimal exposure
- No public services during baseline stage
- Access restricted to internal network
- Physical access retained as emergency fallback

---

## Container Runtime Status

### Docker

- Docker Engine installed
- Service active and enabled
- Running without errors

### Docker Compose

- Docker Compose plugin installed (`docker compose`)
- Multi-service stack deployment validated

### Port Mapping Verification

- Port mapping tested from LAN
- API reachable through port `8000`
- Database not exposed to LAN
- No external exposure configured

---

## Current System State

- Headless server operational
- Remote SSH access functional
- Firewall hardened
- Fail2ban active
- Docker runtime operational
- Docker Compose stack validated
- PostgreSQL container running
- FastAPI container running
- Worker container validated
- LAN access confirmed
- No public service exposure

---

## Known Limitations

- No reverse proxy configured yet
- No monitoring or logging stack implemented
- No Azure integration yet
- No CI/CD pipeline configured
- No public web dashboard implemented

---

## Architectural Direction

The goal is to evolve this baseline into a modular container platform including:

- Containerized application services
- FastAPI service layer
- PostgreSQL database backend
- Background worker for data imports
- Public read-only web dashboard
- Secure hybrid cloud connectivity
- CI/CD-driven deployment workflow
- Structured observability layer

---

## Next Steps

- Prepare web dashboard layer
- Introduce basic logging strategy
- Extend import workflow beyond test data
- Integrate external data sources (EVE Online ESI)
- Update architecture diagrams to reflect the current platform state
