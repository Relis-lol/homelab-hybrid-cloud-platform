# Route Risk Assistant

Route analysis and hauling risk evaluation tool for EVE Online.

Designed to combine route information, cargo characteristics, security status, and combat activity into a practical decision-support system for traders and haulers.

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
| Route Setup         | Start & destination systems   |
| Cargo Analysis      | Cargo value, volume, ISK/m³   |
| Route Options       | Multiple route modes          |
| Risk Evaluation     | Security status analysis      |
| Activity Analysis   | Kill statistics integration   |
| Persistence         | Local scenario storage        |
| Backend Integration | API-assisted route evaluation |

---

# 🧱 Key Design Decisions

* Risk evaluation handled by backend services

  * allows future expansion without frontend changes

* Scenario storage remains local

  * no accounts or user database required

* Multiple risk factors contribute to scoring

  * avoids relying on a single metric

* Designed as a dashboard module

  * integrates directly with other trading tools

---

# 📊 Risk Inputs

Current scoring uses combinations of:

* Security status
* Route length
* Cargo value
* Cargo density (ISK/m³)
* Known dangerous systems
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

# 🔧 Current Risk Levels

| Level  | Meaning                       |
| ------ | ----------------------------- |
| Low    | Minimal route concerns        |
| Medium | Increased caution recommended |
| High   | Elevated risk exposure        |

---

# 💾 Scenario System

Supported through browser local storage.

Features:

* Save route configurations
* Restore previous scenarios
* Persistent local settings
* No authentication required

---

# ⚙️ Tech Stack

* JavaScript
* FastAPI
* PostgreSQL
* EVE ESI API

---

# 📈 Current Status

**Operational**

* Route planning workflow
* Security status evaluation
* Kill-data integration
* Basic risk scoring
* Scenario persistence
* Dashboard integration

---

# 🔮 Planned Expansion

* Dynamic danger ratings
* Historical route intelligence
* Cargo-aware scoring models
* Safer route recommendations
* Regional hauling analytics
* Event-driven risk detection
