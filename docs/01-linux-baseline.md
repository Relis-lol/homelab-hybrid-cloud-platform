# 01 – Linux Baseline Setup

## Hardware

**Model:** NiPoGi 4K Mini PC  
**CPU:** AMD Ryzen 3 4300U (4 cores / 4 threads)  
**RAM:** 16GB DDR4  
**Storage:** 512GB SSD  
**Original OS:** Windows 11 Pro (replaced with Linux for server usage)

Reason for hardware choice:
- Low power consumption
- Always-on capable
- Sufficient CPU & RAM for container workloads
- Cost-efficient homelab foundation

---

## Operating System

Ubuntu Server (minimal installation)

Why Ubuntu Server:
- Stable LTS base
- Lightweight footprint
- Large community support
- Container-friendly ecosystem

---

## Network

- Connected via LAN
- Router-managed IP (static IP planned)
- SSH remote access enabled

---

## Access & Security

- SSH enabled
- Firewall (UFW) activated
- System fully updated
- Remote access tested

---

## Current Limitations

- No Docker containers deployed yet
- No public services exposed
- No database configured
- No Azure integration

---

## Next Steps

- Install Docker & Docker Compose
- Define service architecture
- Plan database layer
- Design hybrid cloud integration concept
