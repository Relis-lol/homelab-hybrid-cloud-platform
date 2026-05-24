# 06 – Observability & Logging

## Objective

Provide visibility into system behavior, failures, and operational health across the platform.

The current observability layer focuses on automated worker execution, infrastructure visibility, and early operational monitoring.

---

## Current Monitoring Features

Implemented components:

- Worker execution tracking
- Discord webhook notifications
- Cron-based execution visibility
- Docker container logs
- API offline detection
- Process count monitoring
- Network traffic monitoring
- Backup milestone creation
- UFW firewall logging
- Fail2ban SSH monitoring

---

## Monitoring Scope

Current monitoring covers:

- Worker success/failure status
- Import duration and row counts
- API availability
- Database write operations
- Docker container behavior
- Process and network activity
- Basic system security events

---

## Worker Monitoring

The worker currently acts as the most observable backend component.

### Execution Tracking

Each worker run stores metadata inside the database, including:

- Start and finish time
- Execution status
- Imported row count
- Error notes

This provides historical visibility into pipeline reliability and import behavior.

---

### Discord Notifications

Worker runs send Discord webhook notifications.

Current behavior:

- Successful imports send summary messages
- Failed runs send error notifications
- Offline/API issues trigger alerts
- Notifications include execution details

### Benefits

- Faster failure detection
- Reduced manual log inspection
- Easier unattended operation monitoring
- Basic operational awareness

---

## Logging Sources

### Database-Level

`price_import_runs` acts as a structured execution log for worker activity.

---

### Container-Level

Docker logs provide runtime visibility for:

- API container
- Worker container
- PostgreSQL container

Example:

```bash
docker compose logs worker
```

---

### System-Level

Current system logging includes:

- UFW firewall events
- Fail2ban SSH protection logs
- Basic Ubuntu system logs
- Process and network monitoring exports

---

## Automation Visibility

Worker execution is handled through cron scheduling.

Current behavior:

- Scheduled automatic imports
- Manual execution still possible
- Failures surfaced through Discord
- Controlled one-shot worker lifecycle
- Monitoring exports generated automatically

This keeps worker execution predictable and easier to debug.

---

## Current Status

Currently operational:

- Worker execution tracking
- Structured import history
- Discord monitoring notifications
- API availability checks
- Docker runtime logging
- Basic process/network monitoring
- Backup milestone tracking
- Basic security monitoring

The platform already supports lightweight operational observability and unattended monitoring workflows.

---

## Known Limitations

- No centralized logging stack
- No Prometheus/Grafana setup
- No advanced metrics dashboard
- No container health dashboard
- No distributed tracing
- No advanced alert escalation
- No formal retention/rotation strategy

---

## Next Steps

- Add structured API request logging
- Introduce centralized log aggregation
- Add lightweight monitoring dashboard
- Implement metrics collection
- Add container health monitoring
- Improve alerting workflows
- Define log retention strategy
- Explore Azure-assisted monitoring later
