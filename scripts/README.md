# Automation & Operations Scripts

Operational helper scripts, maintenance tooling, deployment utilities, and infrastructure automation for the EVE Market Platform.

---

# 🎯 Purpose

Provide repeatable operational workflows for backups, deployments, monitoring, recovery, and infrastructure maintenance.

---

# 🛠️ Planned Script Areas

| Area           | Purpose                                            |
| -------------- | -------------------------------------------------- |
| `backups/`     | Automated backup & recovery workflows              |
| `deployment/`  | Docker rebuild & deployment helpers                |
| `maintenance/` | Cleanup, pruning, validation & repair utilities    |
| `monitoring/`  | Health checks, Discord alerts, runtime diagnostics |
| `database/`    | Import, migration & data maintenance scripts       |

---

# 🧱 Design Decisions

* Scripts stay lightweight and shell-compatible

  * easier debugging on minimal Linux servers

* Critical recovery tooling remains local-only

  * avoids exposing infrastructure internals publicly

* Operational scripts are separated from application logic

  * cleaner architecture and safer maintenance

* Most workflows are designed around Docker Compose

  * reproducible deployments and simpler recovery handling

---

# 🚀 Example Operations

```bash
docker compose logs --tail=120 worker

docker compose build api --no-cache

docker compose up -d

python3 -m py_compile worker.py
```

---

# 🔒 Security Notes

Some operational scripts intentionally remain private and are not included in the public repository.

Examples:

* server-specific backup paths
* webhook credentials
* recovery automation
* infrastructure-sensitive maintenance tooling
