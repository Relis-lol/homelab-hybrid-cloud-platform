# Trade Looper

Hub-to-hub trade analysis system for EVE Online.

Built to identify profitable arbitrage opportunities between major trade hubs using real market snapshots, demand estimation, fee-aware ROI calculations, and cargo logistics metrics.

---

# 🖼️ Preview

![Trade Looper](../assets/trade-looper.png)

---

# 🎯 Purpose

Transform raw market data into actionable trading opportunities ranked by profitability, liquidity, and execution quality.

---

# 🛠️ Core Features

| Area               | Features                       |
| ------------------ | ------------------------------ |
| Arbitrage Analysis | Hub-to-hub trade opportunities |
| Profitability      | Fee-aware ROI calculations     |
| Demand Analysis    | Buy-order demand estimation    |
| Liquidity          | Supply and demand evaluation   |
| Logistics          | Cargo volume calculations      |
| Risk Filtering     | Low-margin deal suppression    |
| Ranking            | Weighted opportunity scoring   |
| Market Coverage    | Major EVE trade hubs           |

---

# 🧱 Key Design Decisions

* Real market snapshots instead of static prices

  * reflects current market conditions

* Fee-aware profitability calculations

  * avoids unrealistic profit estimates

* Demand and supply validation

  * prevents impossible trade recommendations

* Hub-specific analysis

  * excludes irrelevant regional noise

* Expandable scoring architecture

  * supports future anomaly and event detection

---

# 📊 Opportunity Analysis

Current evaluation includes:

* Buy price
* Target sell price
* Profit per unit
* Net profit potential
* ROI after fees
* Source supply
* Buy-order demand
* Cargo volume
* Market score

---

# 💰 Fee Profiles

Supported trading scenarios:

| Profile          | Fee Model |
| ---------------- | --------- |
| Bad Trader       | 11%       |
| Default Estimate | 8.2%      |
| Good Trader      | 5%        |

Allows profitability comparison across different skill and fee situations.

---

# 🚀 Analysis Flow

```text
Market Snapshots
        ↓
Hub Filtering
        ↓
Supply & Demand Evaluation
        ↓
Fee-Aware ROI Calculation
        ↓
Trade Ranking Engine
        ↓
Opportunity Recommendations
```

---

# ⚙️ Tech Stack

* FastAPI
* PostgreSQL
* JavaScript
* EVE ESI API

---

# 📈 Current Status

**Operational**

* Trade opportunity discovery
* Fee-aware profit estimation
* Demand scoring
* Cargo volume integration
* Hub filtering
* Market ranking system
* Interactive frontend workflow

---

# 🔮 Planned Expansion

* MAV15 liquidity analysis
* Estimated liquidation time
* Organic demand modeling
* Event detection
* HOT deal classification
* Market anomaly scanner
* AI-assisted trade commentary
