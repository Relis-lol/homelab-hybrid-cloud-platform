# Trade Looper

Hub-to-hub trade intelligence system for EVE Online.

Built to identify profitable arbitrage opportunities using real market snapshots, demand estimation, fee-aware ROI calculations, liquidity analysis, and cargo logistics metrics.

---

# 🖼️ Preview

![Trade Looper](../assets/trade-looper.png)

---

# 🎯 Purpose

Transform market data into actionable trading opportunities ranked by profitability, liquidity, and execution quality.

---

# 🛠️ Core Features

| Area               | Features                       |
| ------------------ | ------------------------------ |
| Arbitrage Analysis | Hub-to-hub trade opportunities |
| Profitability      | Fee-aware ROI calculations     |
| Demand Analysis    | Buy-order demand estimation    |
| Liquidity          | Supply and demand evaluation   |
| Logistics          | Cargo volume calculations      |
| Risk Filtering     | Low-quality deal suppression   |
| Ranking            | Weighted opportunity scoring   |
| Market Coverage    | Major EVE trade hubs           |

---

# 🧱 Key Design Decisions

* Real market snapshots

  * reflects current market conditions instead of static pricing

* Fee-aware profitability calculations

  * avoids unrealistic profit estimates

* Demand and supply validation

  * filters low-quality opportunities

* Trade-hub focused analysis

  * removes regional noise from non-hub markets

* Multi-factor ranking system

  * profitability alone does not determine recommendation quality

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

# ⚙️ Technology Stack

* FastAPI
* PostgreSQL
* JavaScript
* EVE ESI API

---

# 📈 Current Status

**Live Production Feature**

* Trade opportunity discovery
* Fee-aware profit estimation
* Demand scoring
* Liquidity analysis
* Cargo volume integration
* Trade-hub filtering
* Market ranking system
* Interactive frontend workflow

Used as part of the live platform:

https://eve-tradelooper.com/

---

# 🎯 Engineering Focus

The system prioritizes realistic trading opportunities over raw profit numbers by combining:

* Market demand
* Available supply
* Trading fees
* Cargo efficiency
* Opportunity ranking

This reduces misleading recommendations and produces more practical trading results.
