# Architecture Diagrams

Visual architecture documentation for the EVE Trade Intelligence Platform.

These diagrams complement the technical documentation and provide a high-level view of infrastructure, data movement, service interactions, database structure, and deployment architecture.

---

# 🎯 Purpose

Provide a fast visual overview of how platform components interact.

---

# 📊 Available Diagrams

| File                            | Purpose                                                   |
| ------------------------------- | --------------------------------------------------------- |
| `current-architecture.md`       | Current production architecture and service relationships |
| `data-flow.md`                  | Market ingestion and analytics data flow                  |
| `database-schema.md`            | Core PostgreSQL schema and table relationships            |
| `future-hybrid-architecture.md` | Hybrid-cloud monitoring and deployment architecture       |

---

# 🧱 Diagram Focus Areas

### Infrastructure

* Linux host
* Docker platform
* Service isolation
* Network boundaries
* Public deployment architecture

### Data Flow

* ESI ingestion
* Worker processing
* Database storage
* API delivery
* Frontend consumption

### Database Design

* Market history storage
* Snapshot architecture
* Localization system
* Import tracking
* Relational data structure

### Security

* Cloudflare protection
* Internal networking
* Service separation
* Controlled access layers

### Hybrid Cloud

* Azure Arc integration
* Azure Monitor visibility
* Log Analytics integration
* Hybrid-cloud operations

---

# ⚙️ Diagram Standard

All diagrams use Mermaid and render natively on GitHub.

Benefits:

* Version controlled
* Easy to update
* Lightweight documentation
* GitHub-native rendering
* No external diagram tools required

---

# 🔗 Related Documentation

```text
docs/
frontend/
assets/
```

The diagrams provide visual support for the detailed documentation contained in those directories.
