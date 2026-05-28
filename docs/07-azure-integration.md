# 07 – Azure Hybrid Integration

Planned hybrid-cloud extension for the EVE Market Platform.

The project intentionally follows a hybrid approach where core services remain self-hosted while selected cloud capabilities are added through Azure.

---

# 🎯 Purpose

Explore practical Azure integration without migrating the entire platform into the cloud.

---

# 🧱 Key Design Decisions

* Local infrastructure remains primary

  * critical services continue running on the homelab platform

* Cloud services are added selectively

  * use Azure where it provides clear value

* Hybrid architecture over cloud-only deployment

  * balances learning, cost, and operational control

---

# ☁️ Planned Azure Services

| Service            | Purpose                            |
| ------------------ | ---------------------------------- |
| Azure Blob Storage | Backup and archive storage         |
| Azure Monitor      | Optional observability experiments |
| GitHub Actions     | CI/CD integration                  |
| Terraform / Bicep  | Infrastructure as Code             |

---

# 🏗️ Target Architecture

```text
User
   ↓
Local Platform
   ↕
Azure Services
```

---

# 🚀 Planned First Step

Azure Blob Storage for backup and archival workflows.

This provides a practical hybrid-cloud use case while keeping application workloads local.

---

# 📈 Current Status

**Planning Phase**

Current development priorities remain:

* Platform stability
* Data pipeline improvements
* Dashboard development
* Observability enhancements

Azure integration will begin after the local platform architecture is finalized.

---

# 🔮 Future Expansion

* Cloud backup automation
* Azure-assisted monitoring
* Infrastructure as Code
* CI/CD deployment workflows
* Hybrid deployment experiments
