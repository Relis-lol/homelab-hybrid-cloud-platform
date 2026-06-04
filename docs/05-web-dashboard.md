
# 06 – Observability & Logging

Operational visibility layer for the EVE Trade Intelligence Platform.

Provides monitoring, execution tracking, logging, alerting, and infrastructure visibility across backend services, worker pipelines, cloud monitoring systems, and physical monitoring hardware.

---

# 🎯 Purpose

Detect failures early, monitor platform health, and provide visibility into automated workflows and infrastructure behavior.

---

# 🛠️ Observability Components

| Area | Coverage |
|---|---|
| Worker Monitoring | Import execution tracking |
| Notifications | Discord alerts |
| Runtime Logs | Docker container logs |
| API Monitoring | Availability checks |
| Database Tracking | Import history records |
| Security Events | UFW and Fail2ban logs |
| Scheduling | Cron execution visibility |
| Infrastructure | Host resource monitoring |
| Azure Monitoring | Cloud-based monitoring |
| Cloudflare Analytics | Traffic visibility |
| CYD Display | Physical monitoring dashboard |

---

# 🧱 Key Design Decisions

* Monitoring starts at the worker layer

  * data ingestion is the most critical platform process

* Notifications over manual log inspection

  * failures become visible immediately

* Structured execution tracking

  * import history remains queryable

* Lightweight observability

  * practical visibility without requiring a large monitoring stack

* Hybrid-cloud monitoring

  * infrastructure remains observable remotely

* Security visibility included

  * operational and security monitoring share the same workflow

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
* CPU utilization
* Memory utilization
* Storage utilization
* Network throughput
* System temperature
* Public endpoint availability
* Traffic visibility

---

# 🔄 Worker Monitoring

Tracked information includes:

* Start time
* Completion time
* Execution status
* Imported records
* Error details
* Runtime information

Stored in:

```text
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

# ☁️ Azure Monitoring

Implemented through:

* Azure Arc
* Azure Monitor Agent
* Log Analytics Workspace
* OpenTelemetry

### Current Capabilities

* Hybrid-cloud monitoring
* Heartbeat monitoring
* Offline detection
* Cloud-based log collection
* Resource visibility
* Alerting support

### Cost Control

Monitoring operates behind strict budget limits and alert thresholds to prevent unexpected cloud costs.

---

# 📟 CYD Monitoring Display

A dedicated ESP32 CYD 2.8" display provides real-time infrastructure visibility.

Displayed metrics include:

* API status
* Database status
* Worker status
* CPU utilization
* RAM utilization
* SSD utilization
* Network throughput
* System temperature
* Last synchronization timestamp

Refresh interval:

```text
30 seconds
```

---

# 🌐 Cloudflare Visibility

Cloudflare provides:

* DNS management
* HTTPS protection
* Reverse proxy services
* Basic traffic analytics
* Public endpoint visibility

---

# 📜 Logging Sources

### Database

Structured execution tracking:

```text
price_import_runs
```

### Containers

Runtime visibility for:

* FastAPI
* Worker
* PostgreSQL
* Frontend

Example:

```bash
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

```text
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
* Azure-based monitoring
* Cloudflare traffic visibility
* Real-time hardware monitoring display

---

# 📈 Current Status

**Live Production Observability Layer**

Provides operational visibility for:

* Market ingestion
* Backend services
* Database operations
* Infrastructure health
* Security monitoring
* Public platform availability

Platform URL:

https://eve-tradelooper.com/
