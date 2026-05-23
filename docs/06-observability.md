# 06 – Observability & Logging

## Objective

Provide visibility into system behavior, failures, and operational health across the platform.

The current monitoring setup focuses mainly on the automated worker pipeline and basic infrastructure visibility.

---

## Current Monitoring Features

Implemented components:

- Worker execution tracking
- Discord webhook notifications
- Cron-based execution visibility
- Docker container logs
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
- Basic system security events

---

## Worker Monitoring

The worker is currently the most observable part of the platform.

### Execution Tracking

Each worker run stores metadata in the database, including:

- Start and finish time
- Execution status
- Imported row count
- Error notes

This provides basic historical visibility into pipeline reliability.

---

### Discord Notifications

Worker runs send Discord webhook notifications.

Current behavior:

- Successful imports send summary messages
- Failed runs send error notifications
- Notifications include execution details

### Benefits

- Faster failure detection
- Reduced manual log inspection
- Easier debugging during unattended execution

---

## Logging Sources

### Database-Level

`price_import_runs` acts as a structured execution log.

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
- Basic Ubuntu logs

---

## Automation Visibility

Worker execution is handled through cron scheduling.

Current behavior:

- Scheduled automatic imports
- Manual execution still possible
- Failures surfaced through Discord
- Controlled one-shot worker lifecycle

---

## Current Status

Currently operational:

- Worker execution tracking
- Structured import history
- Discord notifications
- Docker runtime logging
- Basic security monitoring

The platform already supports basic operational debugging and monitoring workflows.

---

## Known Limitations

- No centralized logging
- No metrics dashboard
- No Prometheus/Grafana stack
- No uptime monitoring
- No container health dashboard
- No advanced alerting system
- No log rotation strategy

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
