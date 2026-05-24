# Route Risk Assistant

Browser-based hauling and route analysis tool for EVE Online.

The system combines route information, cargo value, security status analysis, and contextual risk indicators into a modular decision-support tool for traders and haulers.

The project currently includes both frontend systems and early backend route analysis foundations.

## Preview

![Route Risk Setup](../assets/route-risk.png)

![Route Risk Analysis](../assets/route-risk2.png)

---

# Current Features

- Route setup interface
- Cargo and ship profile input
- Route mode selection
- Route analysis API foundation
- Security status detection
- Kill statistics integration
- Basic risk scoring prototype
- Dangerous system identification
- Scenario saving
- Responsive dashboard UI
- Local scenario persistence
- EVE-inspired dark UI design

---

# Current Dashboard Sections

## Route Setup

Supports route configuration between systems.

Current inputs:

- Start system
- Destination system
- Route mode
- Ship type
- Cargo value
- Cargo volume
- Profit per m³
- Avoid/watch systems
- Manual context notes

---

## Risk Analysis

The current system already supports basic backend-assisted route analysis.

### Current Indicators

- Risk score
- Route length
- Cargo ISK per m³
- Security status awareness
- Dangerous system detection
- Basic recommendation level

### Current Risk Levels

- Low Risk
- Medium Risk
- High Risk

---

# Backend Foundation

The project now includes an early backend analysis layer.

### Current Backend Features

- Route analysis endpoint
- System path retrieval
- Security status lookup
- Kill statistics integration
- Basic route scoring prototype

### Current Workflow

```text
Route Request
→ Backend Analysis
→ Security/Kill Evaluation
→ Risk Scoring
→ Recommendation Output
```

---

# Scenario System

The tool supports local scenario persistence through browser storage.

### Current Capabilities

- Save route setups
- Restore previous scenarios
- Lightweight local persistence
- No account system required

---

# Design Goals

The project focuses on:

- Fast route evaluation
- Lightweight browser-based UX
- Expandable risk analysis logic
- Modular dashboard integration
- Practical hauling support tools
- Future backend-assisted analysis

---

# Current Status

Currently operational:

- Frontend route workflow
- Backend route analysis foundation
- Basic scoring prototype
- Kill-data integration
- Security status evaluation
- Scenario persistence
- Dashboard integration

Advanced route intelligence and visualization systems are still planned future expansion areas.

---

# Planned Features

- Dynamic system danger ratings
- Historical route risk tracking
- Cargo-aware route scoring
- Safer route suggestions
- Regional hauling analysis
- AI-assisted hauling recommendations
- Expanded route analytics
