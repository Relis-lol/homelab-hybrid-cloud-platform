# AHN News Network

Dynamic news aggregation and presentation system for the EVE Trade Intelligence Platform.

Designed to transform public EVE Online updates, patch notes, CCP announcements, and lore-related content into short market-oriented news briefs for dashboard presentation.

---

# 🎯 Purpose

Provide contextual market and universe information without replacing data-driven analytics.

---

# 🛠️ Core Features

| Area                | Purpose                                     |
| ------------------- | ------------------------------------------- |
| Public News Sources | CCP news, patch notes, and official updates |
| Lore Context        | Optional worldbuilding and universe events  |
| News Summaries      | Short-form headline generation              |
| Market Presentation | Trading-oriented news delivery              |
| User Control        | Optional enable/disable toggle              |
| Lightweight Runtime | Low-impact processing and delivery          |

---

# 🧱 Key Design Decisions

* Informational rather than predictive

  * does not generate trading recommendations

* Public sources only

  * no account-based or private data collection

* Optional dashboard feature

  * can be disabled independently

* Lightweight processing

  * avoids heavy infrastructure requirements

* Transparent AI disclosure

  * generated and rewritten content is clearly identified

* Separated from analytics systems

  * trading calculations remain fully data-driven

---

# 📰 Example Output

```text id="xlmjua"
YC128 Market Brief:

New industrial directives from empire space are increasing speculation across logistics hubs. Traders are closely monitoring mineral flow, fuel demand, and regional hauling activity.
```

---

# 🚀 Processing Flow

```text id="77rggt"
Public News Sources
        ↓
Source Filtering
        ↓
Content Summarization
        ↓
Market-Oriented Rewrite
        ↓
Dashboard Presentation
        ↓
Optional User Toggle
```

---

# ⚙️ Technology Stack

* Python
* FastAPI
* Frontend News Components
* Public News Sources
* AI-Assisted Text Processing

---

# 📈 Current Status

**Live Production Feature**

* Dashboard-integrated news feed
* Public source aggregation
* Short-form news summaries
* Market-oriented presentation
* User-controlled visibility
* AI disclosure integration

Used as an optional contextual information layer within:

https://eve-tradelooper.com/

---

# 🎯 Engineering Focus

The system enhances platform presentation and immersion while remaining completely separated from trading calculations, rankings, and recommendation logic.

Market intelligence remains data-driven. The news layer provides context only.
