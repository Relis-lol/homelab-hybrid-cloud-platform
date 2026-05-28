# Market Newsfeed

Lightweight RP-style news layer for the EVE Market Platform.

Designed to transform public EVE Online updates, patch notes, CCP news, and lore-related information into short atmospheric trading-news snippets for dashboard immersion.

---

# 🎯 Purpose

Add optional worldbuilding and market atmosphere without turning the platform into an automated financial advisor.

---

# 🛠️ Planned Features

| Area                | Purpose                                                |
| ------------------- | ------------------------------------------------------ |
| Public News Sources | Read CCP news, patch notes, and official updates       |
| Lore Context        | Include worldbuilding flavor where relevant            |
| News Rewriting      | Convert long updates into short market-style headlines |
| Trading Flavor      | Present updates as an in-universe trade news channel   |
| Toggle Control      | Allow users to disable the feature                     |
| Lightweight Runtime | Keep processing small and non-critical                 |

---

# 🧱 Design Decisions

* Decorative and informational only

  * not used as direct trading advice

* Public sources only

  * no private scraping or account-based data

* Optional feature

  * can be disabled without affecting core tools

* Lightweight implementation

  * avoids heavy AI workloads on the main platform

* Clear AI disclosure

  * rewritten or generated text is marked transparently

* Separated from trade calculations

  * market recommendations remain data-driven, not lore-driven

---

# 📰 Example Output Style

```text
YC128 Market Brief:
New industrial directives from empire space are stirring speculation across logistics hubs. Traders are watching mineral flow, fuel demand, and regional hauling pressure.
```

---

# 🚀 Planned Flow

```text
Public CCP / Patch / Lore Sources
        ↓
Source Filtering
        ↓
Short Summary Generation
        ↓
RP Trading-News Rewrite
        ↓
Dashboard News Ticker
        ↓
Optional User Toggle
```

---

# ⚙️ Planned Tech

* Python Worker
* FastAPI Endpoint
* Public Web Sources / RSS
* Lightweight AI or rule-based rewriting
* Frontend News Ticker

---

# 📈 Current Status

**Planning Phase**

The system is planned as an optional dashboard feature for immersion, context, and presentation polish.

---

# 🔮 Future Expansion

* Source attribution links
* Manual moderation mode
* Event impact tags
* Category filters
* Market anomaly pairing
* Discord news summaries
