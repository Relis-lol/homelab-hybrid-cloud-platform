# 06 – Observability & Logging

## Objective

Ensure visibility into system behavior, performance, and failures across all components.

---

## Current Observability (Implemented)

* Worker execution tracking via `price_import_runs`
* Discord webhook notifications for worker success and failure
* Cron-based job execution visibility
* Basic UFW logging enabled
* Fail2ban active for SSH protection
* Docker container logs accessible via `docker compose logs`

---

## Monitoring Scope

* Worker job execution (success / failure / duration)
* Import pipeline consistency
* API request behavior
* Container health status
* Resource usage (CPU / RAM)

---

## Worker Monitoring Model

The worker acts as the central observable component of the data pipeline.

### Execution Tracking

Each run is recorded in the database:

* Start time
* End time
* Status (success / failure)
* Notes (e.g. imported row count)

### External Notification

Worker sends status updates via Discord webhook:

* Successful import → summary message
* Failed import → error message

### Benefits

* Immediate visibility of pipeline status
* No need to manually inspect logs
* Early detection of failures

---

## Logging Sources

### Database-level

* `price_import_runs` acts as structured execution log

### Container-level

* Docker logs for API and worker processes

### System-level

* UFW firewall logs
* Fail2ban logs for SSH access protection

---

## Automation Visibility

Cron-based execution provides predictable scheduling.

### Current Behavior

* Worker runs at defined intervals (e.g. hourly)
* Failures are surfaced via Discord
* Manual execution remains possible for debugging

---

## Current Status

Partial but functional observability layer.

* Worker execution fully traceable
* External notifications active
* Logging available at multiple system layers
* Basic monitoring foundation established

---

## Known Limitations

* No centralized log aggregation
* No structured API request logging
* No metrics collection (Prometheus/Grafana)
* No alerting beyond Discord webhook
* No uptime or health-check monitoring
* No log retention or rotation strategy

---

## Next Steps

* Introduce structured logging in API (request/response logging)
* Aggregate Docker logs into a central system
* Add lightweight monitoring (e.g. Netdata)
* Introduce metrics collection (Prometheus + Grafana)
* Implement alerting beyond Discord (optional escalation)
* Define log retention and rotation strategy
