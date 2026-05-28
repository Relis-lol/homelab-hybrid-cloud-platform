# 07 – Hybrid Cloud Planning

Future hybrid-cloud roadmap for the EVE Market Platform.

The platform is intentionally designed around a self-hosted architecture, with selected cloud services evaluated where they provide practical operational value.

---

# 🎯 Purpose

Explore cloud technologies without moving the core platform away from the local infrastructure.

---

# 🧱 Current Strategy

* Local server remains the primary platform
* Critical services stay self-hosted
* Cloud services are added selectively
* Avoid unnecessary hosting costs
* Focus on practical learning and operational benefits

---

# ☁️ Planned Cloud Areas

| Area           | Purpose                         |
| -------------- | ------------------------------- |
| Monitoring     | Azure Monitor experiments       |
| Backups        | Optional cloud archive storage  |
| Automation     | GitHub Actions integration      |
| Infrastructure | Infrastructure-as-Code learning |

---

# 🏗️ Target Architecture

```text
User
   ↓
Local Platform
   ↕
Selected Cloud Services
```

The local platform continues handling:

* PostgreSQL
* FastAPI
* Worker services
* Frontend applications
* Market analytics

---

# 🚀 Planned First Step

Azure Monitor integration for infrastructure visibility and operational monitoring.

This provides practical cloud experience without increasing application complexity.

---

# 📈 Current Status

**Planning / Research Phase**

Current development priorities remain:

* Platform stability
* Analytics features
* Monitoring improvements
* Automation workflows
* Deployment hardening

No production cloud services are currently required for normal platform operation.

---

# 🔮 Future Exploration

* Azure Monitor
* Cloud backup workflows
* GitHub Actions automation
* Terraform experiments
* Bicep experiments
* Hybrid-cloud learning projects
