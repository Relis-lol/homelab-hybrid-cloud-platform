# 06 – Observability & Logging

## Objective

Provide visibility into system behavior, failures, and operational health across the platform.

The observability layer helps monitor the automated data pipeline, detect failures early, and support long-term maintainability of the system.

---

## Current Observability (Implemented)

Currently implemented monitoring and logging features:

* Worker execution tracking via `price_import_runs`
* Discord webhook notifications for worker success/failure
* Cron-based scheduled execution visibility
* Docker container logs accessible through Docker Compose
* Basic UFW firewall logging
* Fail2ban protection and SSH event logging

---

## Monitoring Scope

The current monitoring model focuses on operational visibility for the most important platform components.

### Current Monitoring Areas

* Worker execution status
* Import success/failure tracking
* API availability
* Docker container behavior
* Database write operations
* Import duration and row counts
* Basic system-level security activity

---

## Worker Monitoring Model

The worker is currently the most observable component in the platform because it represents the core automated data ingestion pipeline.

---

### Execution Tracking

Each worker execution stores structured metadata inside the database.

Tracked information includes:

* Start time
* End time
* Execution status
* Imported row count
* Error notes when failures occur

This allows historical visibility into import behavior and pipeline reliability.

---

### Discord Notifications

Worker executions send Discord webhook notifications.

Current notification behavior:

* Successful import runs send summary messages
* Failed imports send error notifications
* Notifications include execution details and status information

---

### Benefits

The current setup provides:

* Immediate visibility into worker failures
* Reduced need for manual log inspection
* Faster debugging during pipeline issues
* Basic operational awareness for unattended execution

---

## Logging Sources

### Database-Level Logging

The `price_import_runs` table acts as a structured execution log for the import pipeline.

---

### Container-Level Logging

Docker logs provide runtime visibility for:

* API container
* Worker container
* PostgreSQL container

Typical usage:

```bash
docker compose logs api
docker compose logs worker
```

---

### System-Level Logging

Current system logging includes:

* UFW firewall activity
* Fail2ban SSH protection events
* Basic Ubuntu system logs

---

## Automation Visibility

The worker currently runs through cron-based scheduling.

### Current Scheduling Behavior

* Worker executes automatically at defined intervals
* Manual execution remains possible
* Failures surface through Discord notifications
* Worker lifecycle follows a controlled one-shot execution model

This model avoids permanently running background containers and simplifies failure handling.

---

## Current Status

A functional observability foundation is already established.

Currently operational:

* Worker execution tracking
* Structured import run history
* Discord-based notifications
* Cron execution visibility
* Docker runtime logs
* Basic security monitoring

The platform already supports basic operational monitoring and debugging workflows.

---

## Known Limitations

Current limitations include:

* No centralized log aggregation
* No structured API request logging
* No metrics collection stack
* No Grafana/Prometheus integration
* No advanced alerting system
* No uptime monitoring
* No health-check dashboard
* No log retention or rotation strategy

---

## Planned Improvements

Planned future improvements include:

* Structured API request logging
* Centralized log aggregation
* Lightweight monitoring dashboard (e.g. Netdata)
* Prometheus metrics collection
* Grafana dashboards
* Container health monitoring
* Extended alerting workflows
* Log retention and rotation strategy
* Optional cloud-assisted monitoring through Azure integration
