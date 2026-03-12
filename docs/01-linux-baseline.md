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
- Router-managed static IP planned
- No public ports exposed
- No port forwarding configured

### Rationale

- LAN-only exposure reduces attack surface
- Router-level static IP is preferred over OS-level static configuration for this setup
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

**Impact:**

- SSH is no longer broadly allowed
- Attack surface is reduced
- No external SSH exposure is possible through current network configuration

### Fail2ban

- Installed and enabled
- SSH jail active with default configuration

**Objective:**  
Mitigate brute-force attempts even in internal network scenarios.

---

## System Hardening

- System fully updated with `apt update && apt upgrade`
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

- Docker Compose installed
- Multi-service stack deployment validated

### Port Mapping Verification

- Port mapping tested from LAN
- API reachable through port `8000`
- Database not exposed to LAN
- No external exposure configured

---

## Current System State

- Headless operation confirmed
- Remote access fully functional
- Firewall hardened
- Fail2ban active
- Docker operational
- Docker Compose operational
- PostgreSQL container running
- FastAPI container running
- Worker container validated
- LAN access validated
- No public exposure

---

## Known Limitations

- Static IP not yet enforced at router level
- No reverse proxy configured
- No monitoring or logging stack
- No Azure integration
- No CI/CD pipeline
- No public web dashboard yet

---

## Architectural Direction

The goal is to evolve this baseline into:

- Containerized application platform
- API service layer
- PostgreSQL database backend
- Background worker for scheduled imports
- Public read-only web dashboard
- Secure hybrid cloud connectivity
- CI/CD-driven deployment workflow
- Structured observability layer

---

## Next Steps

- Enforce static IP at router level
- Prepare web dashboard layer
- Introduce basic logging strategy
- Extend import workflow beyond test data
- Update architecture diagrams to reflect the current platform state
