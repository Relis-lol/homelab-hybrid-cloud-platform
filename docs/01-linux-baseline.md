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
- Suitable for virtualization & Docker-based services

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

### Firewall

- UFW enabled
- Only OpenSSH allowed
- Default deny policy for incoming connections

### System Hardening

- System fully updated (`apt update && apt upgrade`)
- Timezone configured
- Power button configured for clean shutdown
- No unnecessary services installed

### Security Philosophy

- Principle of minimal exposure
- No public services at baseline stage
- Access restricted to key-based SSH only
- Physical access retained as emergency fallback

---

## Current System State

- Headless operation confirmed
- Remote access fully functional
- Stable uptime
- No containers deployed yet
- No external dependencies configured

---

## Known Limitations

- No static IP enforced yet
- No container runtime installed
- No database layer
- No monitoring / logging stack
- No Azure integration

---

## Architectural Direction

The goal is to evolve this baseline into:

- Containerized application platform
- API service layer
- PostgreSQL database backend
- Public read-only web dashboard
- Secure hybrid cloud connectivity
- CI/CD-driven deployment workflow

---

## Next Steps

- Enforce static IP at router level
- Install Docker Engine
- Install Docker Compose
- Deploy first test container
- Document container lifecycle management

