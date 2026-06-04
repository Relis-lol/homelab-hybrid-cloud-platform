# Trade Cargo Calculator

Browser-based logistics and profitability calculator for EVE Online traders and haulers.

Built to support fast decision-making during station trading, hauling operations, and cargo planning without requiring backend services or market API access.

---

# 🖼️ Preview

![Trade Calculator](../assets/trade-calc.png)

---

# 🎯 Purpose

Estimate cargo capacity, trade profitability, and transport efficiency within seconds.

---

# 🛠️ Core Features

| Area               | Features                                 |
| ------------------ | ---------------------------------------- |
| Cargo Planning     | Multi-ship cargo management              |
| Capacity Analysis  | Maximum purchasable quantity calculation |
| Profitability      | Buy vs. sell profit estimation           |
| Trading Costs      | Fee and tax simulation                   |
| Efficiency Metrics | Profit per unit and profit per m³        |
| Quantity Control   | Manual amount overrides                  |
| Utility Tools      | Integrated side calculator               |
| Input Handling     | Smart market number parsing              |
| Persistence        | Local browser storage                    |

---

# 🧱 Key Design Decisions

* Fully client-side architecture

  * no backend dependency

* Designed for active gameplay usage

  * minimal clicks and fast calculations

* Local persistence only

  * no accounts or user data collection

* Supports multiple hauling scenarios

  * single ship and fleet cargo planning

* Lightweight implementation

  * instant calculations without API calls

---

# 📊 Supported Trading Workflows

* Cargo run planning
* Station trading calculations
* Multi-ship logistics planning
* Capacity optimization
* Margin comparison
* Profitability estimation

---

# 🔢 Smart Number Parsing

Supported formats:

```text
1.5m
250k
2b
1250000
```

Automatically converts common EVE market notation into usable values.

---

# 💾 Local Persistence

Stored in browser LocalStorage:

* Ship counts
* Cargo capacities
* Calculator preferences
* Previous calculation values

No backend, database, or account system required.

---

# 🚀 Example Workflow

```text
Cargo Capacity
    ↓
Market Price
    ↓
Trading Fees
    ↓
Profit Analysis
    ↓
Profit per m³
    ↓
Transport Decision
```

---

# ⚙️ Technology Stack

* HTML5
* CSS3
* Vanilla JavaScript
* LocalStorage

---

# 📈 Current Status

**Completed**

* Cargo calculations
* Profit estimation
* Multi-ship support
* Fee simulation
* Profit-per-m³ analysis
* Smart number parsing
* Local persistence
* Browser-only execution

The calculator remains a lightweight standalone utility focused on practical trading and hauling workflows.
