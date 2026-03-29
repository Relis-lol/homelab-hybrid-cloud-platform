# 06 – Observability & Logging

## Objective

Ensure visibility into system behavior, performance, and failures.

---

## Current Observability (Already Exists)

- Worker execution tracking via `price_import_runs`
- Basic UFW logging
- Fail2ban active for SSH protection
- Docker container logs accessible

---

## Monitoring Scope

- Import job success/failure
- API request behavior
- Container health
- Resource usage (CPU / RAM)

---

## Planned Components

- Centralized log aggregation
- Structured API request logging
- Basic metrics dashboard
- Log rotation and retention strategy

---

## Current Status

Partial observability implemented.

- Import tracking already functional
- System-level security monitoring active

---

## Next Steps

- Introduce structured logging in API
- Aggregate Docker logs
- Add lightweight monitoring (e.g. Netdata or Prometheus later)
