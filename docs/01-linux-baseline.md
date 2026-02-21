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
- Upgradeable RAM & storage
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

- Long-Term Support (5 years security updates)
- Stable and widely adopted in production environments
- Strong Docker and cloud ecosystem compatibility
- Large documentation base

---

## Network Configuration

- Wired LAN connection (no WiFi usage)
- DHCP assigned IP: 192.168.178.47
- Router-managed static IP planned
- No public ports exposed
- No port forwarding configured

### Rationale

- LAN-only exposure reduces attack surface
- Router-level static IP preferred over OS-level static config
- Server remains private within internal network

---

## Access & Security Model

### SSH Configuration

- ED25519 key pair generated on client machine
- Public key added to `~/.ssh/authorized_keys`
- Key-based authentication verified
- PasswordAuthentication disabled
- PermitRootLogin disabled
- PubkeyAuthentication enforced

### Firewall (UFW)

- UFW enabled
- Default policy: deny incoming / allow outgoing
- SSH (22/tcp) allowed **only from 192.168.178.0/24**
- Port 8080 allowed from 192.168.178.0/24
- Logging enabled (low level)

#### Security Adjustment

Removed default OpenSSH profile rule and restricted SSH access to local subnet only.

**Impact:**
- SSH no longer broadly allowed
- Reduced internal attack surface
- No external exposure possible

### Fail2ban

- Installed and enabled
- SSH jail active with default configuration

Objective:
Mitigate brute-force attempts even within internal network scenarios.

---

## System Hardening

- System fully updated (`apt update && apt upgrade`)
- Timezone configured
- No unnecessary services installed
- Headless operation enforced

### Security Philosophy

- Principle of minimal exposure
- No public services at baseline stage
- Access restricted to key-based SSH only
- Physical access retained as emergency fallback

---

## Container Runtime Status

### Docker

- Docker Engine installed
- Service active and enabled
- Running without errors

### Docker Compose

- Compose installed
- Test stack deployed successfully

### Port Mapping Verification

- Container port mapping tested
- Access confirmed from LAN
- No external exposure configured

---

## Current System State

- Headless operation confirmed
- Remote access fully functional
- Firewall hardened
- Fail2ban active
- Docker operational
- Compose operational
- LAN access validated
- No public exposure

---

## Known Limitations

- Static IP not yet enforced at router level
- No production container stack deployed
- No database layer configured
- No monitoring / logging stack
- No Azure integration
- No CI/CD pipeline

---

## Architectural Direction

The goal is to evolve this baseline into:

- Containerized application platform
- API service layer
- PostgreSQL database backend
- Public read-only web dashboard
- Secure hybrid cloud connectivity
- CI/CD-driven deployment workflow
- Structured observability layer

---

## Next Steps

- Enforce static IP at router level
- Deploy PostgreSQL container
- Define API service structure
- Introduce basic logging strategy
- Prepare architecture diagram draft
