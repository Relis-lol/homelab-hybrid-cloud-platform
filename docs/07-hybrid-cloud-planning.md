
# 07 – Hybrid Cloud Planning

Hybrid-cloud integration layer for the EVE Trade Intelligence Platform.

The platform is intentionally designed around a self-hosted architecture, with selected cloud services used where they provide practical operational value.

---

# 🎯 Purpose

Gain hands-on cloud experience while keeping core infrastructure, applications, and data pipelines self-hosted.

---

# 🧱 Hybrid-Cloud Strategy

* Local server remains the primary platform
* Critical services stay self-hosted
* Cloud services are added selectively
* Operational visibility takes priority over cloud hosting
* Focus on practical learning and operational benefits

---

# ☁️ Implemented Cloud Services

| Area | Technology | Purpose |
|---|---|---|
| Hybrid Management | Azure Arc | Cloud-based server management |
| Monitoring | Azure Monitor | Infrastructure visibility |
| Logging | Log Analytics Workspace | Centralized telemetry |
| Observability | OpenTelemetry | Monitoring integration |

---

# 🏗️ Hybrid Architecture

```text
User
   ↓
Cloudflare
   ↓
Local Platform
   ↕
Azure Monitoring Services
```

The local platform continues handling:

* PostgreSQL
* FastAPI
* Worker services
* Frontend applications
* Market analytics
* Data storage

Azure currently provides:

* Monitoring
* Resource visibility
* Heartbeat tracking
* Log collection
* Alerting support

---

# 🚀 Key Design Decisions

* Cloud services complement local infrastructure

  * core workloads remain self-hosted

* Monitoring before migration

  * operational visibility delivers immediate value

* Cost-controlled cloud adoption

  * avoid unnecessary recurring costs

* Learning through real infrastructure

  * cloud services are integrated into a production environment

---

# 📊 Current Cloud Footprint

Implemented:

* Azure Arc connected server
* Azure Monitor Agent
* Log Analytics Workspace
* OpenTelemetry integration
* Cost monitoring and alerting

Not implemented:

* Cloud-hosted databases
* Cloud-hosted applications
* Cloud storage dependencies
* Cloud compute workloads

---

# 📈 Current Status

**Operational Hybrid-Cloud Environment**

The platform remains fully functional without Azure.

Azure currently enhances:

* Infrastructure visibility
* Operational monitoring
* Resource tracking
* Hybrid-cloud management

Platform URL:

https://eve-tradelooper.com/

---

# 🎯 Engineering Focus

The project demonstrates how cloud services can be integrated into an existing self-hosted platform without migrating core workloads, creating a practical hybrid-cloud architecture focused on monitoring, observability, and operational management.
