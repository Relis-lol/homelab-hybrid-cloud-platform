# 08 – Automation & Operations

Operational automation systems supporting the EVE Trade Intelligence Platform.

The platform relies on lightweight automation focused on reliability, repeatability, monitoring, and unattended operation rather than full CI/CD pipelines.

---

# 🎯 Purpose

Reduce manual operations, improve operational consistency, and support reliable platform maintenance.

---

# 🧱 Existing Automation

### Scheduling

* Cron-based worker execution
* `flock`-protected worker execution
* Automated market imports
* Scheduled snapshot generation
* Automated newsfeed updates
* Daily pruning for high-volume market tables
* Controlled batch execution

### Deployment

* Docker Compose deployment
* Reproducible container builds
* Environment-driven configuration

### Monitoring

* Discord notifications
* Azure monitoring integration
* CYD hardware monitoring display
* Automated health visibility

### Backup & Recovery

* GitHub-based source backup
* Local SSD backup workflows
* Backup storage pressure checks
* Instant-restore backup copy outside the normal deletion rotation
* Recovery-oriented deployment structure

---

# 🛠️ Automation Architecture

```text
Cron
   ↓
flock lock
   ↓
Worker Execution
   ↓
Database Updates
   ↓
Analytics Generation
   ↓
Discord Notifications

Docker Compose
   ↓
Service Deployment

Azure Monitor
   ↓
Health Visibility

CYD Display
   ↓
Live Infrastructure Metrics
```

---

# 🧱 Key Design Decisions

* Batch-based automation

  * easier debugging and recovery

* Environment-driven configuration

  * runtime behavior remains configurable

* Reproducible deployments

  * containers can be rebuilt consistently

* Operational simplicity

  * automation without unnecessary complexity

* Monitoring integrated into workflows

  * operational visibility remains part of normal platform operation

* Production safety before feature speed

  * retention, backup checks, internal-only ports and generic API errors reduce operational risk

---

# ⚙️ Configuration Management

Configuration is separated from application code through environment variables.

Examples include:

* Database credentials
* Worker configuration
* Monitoring settings
* Feature toggles

---

# 🔧 Reliability Improvements

After several weeks of stable production use, a focused architecture and operations review was performed. The goal was not to add new features, but to reduce long-term risk in the running platform.

Key improvements:

* Added retention and pruning for high-volume market tables
* Added `flock` protection to prevent overlapping worker runs
* Removed direct public exposure of API container ports
* Moved database credentials toward environment-driven configuration
* Replaced raw client-facing exception details with generic production errors
* Added log rotation guidance for worker, DDNS, pruning and platform logs
* Improved backup pressure checks and restore-oriented backup handling

The largest operational cleanup removed more than 100 million unnecessary duplicate rows caused by overlapping scheduled workers. The worker pipeline now skips a run when the previous execution is still active instead of starting another importer in parallel.

---

# 🚀 Current Capabilities

* Scheduled market imports
* Worker concurrency protection
* Automated snapshot generation
* Automated retention and pruning
* Automated newsfeed updates
* Dockerized deployment workflow
* Environment-based configuration
* Discord alerting
* Azure monitoring integration
* Hardware monitoring display
* GitHub disaster-recovery backup
* Local backup and restore workflow
* Repeatable platform startup

---

# 📈 Current Status

**Operational Automation Layer**

Supports:

* Market ingestion
* Analytics generation
* Platform monitoring
* Alerting workflows
* Backup procedures
* Service deployment

Platform URL:

https://eve-tradelooper.com/

---

# 🎯 Engineering Focus

Automation was intentionally kept lightweight and maintainable.

The platform prioritizes reliability, observability, reproducibility, and operational simplicity over complex enterprise CI/CD tooling.
