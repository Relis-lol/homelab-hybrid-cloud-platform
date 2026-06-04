# Hauling Intelligence

Route analysis and hauling risk evaluation system for EVE Online.

Combines route information, cargo characteristics, security status, and combat activity into a practical decision-support tool for traders and haulers.

---

# 🖼️ Preview

![Route Risk Setup](../assets/route-risk.png)

![Route Risk Analysis](../assets/route-risk2.png)

---

# 🎯 Purpose

Estimate hauling risk before moving valuable cargo through New Eden.

---

# 🛠️ Current Capabilities

| Area                | Features                      |
| ------------------- | ----------------------------- |
| Route Planning      | Start and destination systems |
| Cargo Analysis      | Cargo value, volume, ISK/m³   |
| Route Options       | Multiple route modes          |
| Security Analysis   | Security status evaluation    |
| Activity Analysis   | Kill statistics integration   |
| Risk Scoring        | Multi-factor risk assessment  |
| Persistence         | Local scenario storage        |
| Backend Integration | API-assisted route evaluation |

---

# 🧱 Key Design Decisions

* Backend-driven risk evaluation

  * allows scoring logic to evolve independently of the frontend

* Local scenario storage

  * no accounts or user database required

* Multi-factor scoring model

  * combines route, cargo, security, and activity data

* Dashboard integration

  * operates alongside analytics and trading tools

---

# 📊 Risk Inputs

Current scoring considers:

* Security status
* Route length
* Cargo value
* Cargo density (ISK/m³)
* Dangerous systems
* Recent kill activity

---

# 🚀 Analysis Flow

```text
Route Request
    ↓
Backend Analysis
    ↓
Security Evaluation
    ↓
Kill Activity Review
    ↓
Risk Scoring
    ↓
Recommendation Output
```

---

# 🔧 Risk Levels

| Level  | Meaning                       |
| ------ | ----------------------------- |
| Low    | Minimal route concerns        |
| Medium | Increased caution recommended |
| High   | Elevated risk exposure        |

---

# 💾 Scenario Persistence

Stored locally in the browser.

Features:

* Save route configurations
* Restore previous scenarios
* Persistent local settings
* No authentication required

---

# ⚙️ Technology Stack

* JavaScript
* FastAPI
* PostgreSQL
* EVE ESI API

---

# 📈 Current Status

**Integrated Dashboard Module**

* Route planning workflow
* Security status evaluation
* Kill activity integration
* Risk scoring engine
* Scenario persistence
* Backend integration
* Dashboard integration

Used as part of the live production platform:

https://eve-tradelooper.com/
