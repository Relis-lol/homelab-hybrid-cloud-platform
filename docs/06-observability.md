# 06 – Observability & Logging

Operational visibility layer for the EVE Market Platform.

Provides monitoring, execution tracking, logging, and failure visibility across backend services, worker pipelines, and infrastructure components.

---

# 🎯 Purpose

Detect failures early, monitor platform health, and provide visibility into automated workflows.

---

# 🛠️ Current Observability Components

| Area              | Coverage                  |
| ----------------- | ------------------------- |
| Worker Monitoring | Import execution tracking |
| Notifications     | Discord alerts            |
| Runtime Logs      | Docker container logs     |
| API Monitoring    | Availability checks       |
| Database Tracking | Import history records    |
| Security Events   | UFW and Fail2ban logs     |
| Scheduling        | Cron execution visibility |
| Infrastructure    | Basic host monitoring     |

---

# 🧱 Key Design Decisions

* Monitoring starts at the worker layer

  * data ingestion is the most critical platform process

* Notifications over manual log inspection

  * failures become visible immediately

* Structured execution tracking

  * import history remains queryable

* Lightweight observability first

  * avoids unnecessary complexity during early development

* Security events included

  * operational and security visibility share the same workflow

---

# 📊 Monitoring Scope

Current monitoring covers:

* Worker execution status
* Import duration
* Imported row counts
* API availability
* Database write operations
* Docker container activity
* Scheduled task execution
* Security-related events

---

# 🔄 Worker Monitoring

The worker is currently the most observable platform component.

Tracked information includes:

* Start time
* Completion time
* Execution status
* Imported records
* Error details
* Runtime information

Stored in:

```text id="ykq86p"
price_import_runs
```

---

# 🔔 Notification System

Discord webhooks provide operational alerts.

### Current Events

* Successful imports
* Failed imports
* API availability issues
* Worker execution summaries

### Benefits

* Faster issue detection
* Reduced manual monitoring
* Improved unattended operation
* Lightweight alerting workflow

---

# 📜 Logging Sources

### Database

Structured execution tracking:

```text id="z3ntga"
price_import_runs
```

### Containers

Runtime visibility for:

* FastAPI
* Worker
* PostgreSQL

Example:

```bash id="w4yb1u"
docker compose logs worker
```

### Host System

* UFW firewall logs
* Fail2ban events
* Ubuntu system logs
* Scheduled task execution

---

# ⚙️ Automation Visibility

Worker execution is managed through scheduled cron jobs.

Current workflow:

```text id="ls4jzb"
Cron Schedule
      ↓
Worker Execution
      ↓
Database Tracking
      ↓
Discord Notification
```

This creates a complete audit trail for import operations.

---

# 🚀 Current Capabilities

* Worker execution tracking
* Import history storage
* Discord alerting
* API availability checks
* Docker logging
* Security event visibility
* Scheduled-job monitoring

---

# ⚠️ Current Limitations

* No centralized log aggregation
* No Prometheus metrics
* No Grafana dashboards
* No distributed tracing
* Limited container health monitoring
* No formal log-retention strategy

---

# 🔮 Planned Expansion

* Structured API request logging
* Centralized log collection
* Metrics dashboards
* Container health monitoring
* Alert escalation workflows
* Azure Monitor evaluation
* Long-term retention policies
