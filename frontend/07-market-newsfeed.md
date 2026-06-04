# AHN News Network

Dynamic news aggregation and presentation system for the EVE Trade Intelligence Platform.

Designed to transform public EVE Online updates, CCP announcements, patch notes, logistics-loss intelligence, and in-universe lore into short market-oriented news broadcasts for dashboard presentation.

---

# 🖼️ Preview

![AHN News Network](../assets/ahn-news-network.png)

---

# 🎯 Purpose

Provide contextual market and universe information without influencing trade calculations, rankings, or recommendation logic.

---

# 🛠️ Core Features

| Area | Purpose |
|---|---|
| CCP News Sources | Official news, patch notes, and updates |
| zKillboard Signals | Logistics-loss and hauling-risk bulletins |
| Lore Dataset | Permanent universe and market background entries |
| Local AI Rewrite | Ollama/Qwen-assisted news rewriting |
| Feed Builder | Mixed-source rotation and content balancing |
| Frontend Presentation | Presenter, news bubble, and visual overlays |
| User Control | Optional enable/disable toggle |
| Automation | Scheduled feed generation and updates |
| Failure Handling | Independent source fallback behavior |

---

# 🧱 Key Design Decisions

* Informational rather than predictive

  * does not generate trading recommendations

* Public sources only

  * no account-based or private data collection

* Local AI processing

  * official updates are rewritten locally without external AI services

* Source separation

  * lore, CCP updates, and logistics-loss reports are processed independently

* Failure-tolerant architecture

  * one unavailable source does not break the complete feed

* Optional dashboard module

  * can be disabled without affecting platform functionality

* Analytics isolation

  * trading calculations remain fully data-driven

---

# 📰 Feed Sources

| Source | Usage |
|---|---|
| CCP News | Official news summaries |
| CCP Patch Notes | Update and balance summaries |
| zKillboard API | Logistics-loss and hauling bulletins |
| Lore Dataset | Fallback and atmosphere content |
| Ollama / Qwen | AI-assisted rewriting of official updates |

---

# 🚀 Processing Flow

```text
CCP News / Patch Notes
        ↓
Local AI Rewrite

zKillboard Logistics Signals
        ↓
Loss Classification

Lore Dataset
        ↓
Fallback Rotation

        ↓
Feed Builder
        ↓
JSON Feed Generation
        ↓
Dashboard Presentation
```

---

# ⚙️ Technology Stack

* Python
* FastAPI
* JavaScript
* zKillboard API
* CCP News Sources
* RSS Processing
* Ollama
* Qwen
* JSON Feed Generation
* Cron Automation

---

# 📊 System Components

Implemented functionality:

* Animated frontend news presenter
* Floating cube visual integration
* Rotating news bubble system
* Intro overlays and category banners
* 108 permanent lore entries
* Official CCP news ingestion
* Official patch-note ingestion
* zKillboard logistics-loss bulletins
* AI-assisted content rewriting
* JSON feed generation pipeline
* Cron-based hourly automation
* Source separation and fallback handling

---

# 📈 Current Status

**Live Production Feature**

* Dashboard-integrated news feed
* AI-assisted content generation
* Public source aggregation
* Automated hourly updates
* User-controlled visibility
* Failure-tolerant feed pipeline
* Frontend presentation system

Used as an optional contextual information layer within:

https://eve-tradelooper.com/

---

# 🎯 Engineering Focus

The AHN system demonstrates integration across APIs, automation, AI processing, backend services, and frontend presentation.

Market intelligence remains data-driven. The news layer provides context, atmosphere, and situational awareness while remaining completely separated from trading calculations and recommendation logic.
