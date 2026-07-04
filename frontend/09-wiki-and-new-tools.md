# Wiki & New Tool Expansion

Recent frontend expansion focused on turning the platform from a market dashboard into a broader EVE intelligence workspace.

The new systems keep the same lightweight frontend approach: no user accounts, no framework-heavy client, browser-first interaction, and API-backed calculations where live data is required.

---

# 🖼️ Preview

![Wiki Overview](../assets/wiki-overview-2026-07-04.png)

![Current UI Screenshot Overview](../assets/tab-screenshots-2026-07-04/contact-sheet.png)

---

# 🎯 Purpose

Support continued platform growth without forcing every new feature into the original market-dashboard workflow.

The Wiki gives static reference content a clear home, while newer tools cover paste-driven analysis, Pochven activity, ESS planning, and gank profitability.

---

# 🛠️ Included Systems

| System | Purpose |
|---|---|
| Wiki | Static EVE knowledge base, guides, and tool context |
| OmniScanner | Detects pasted cargo, mining, D-Scan, and Local input |
| Trig WH Finder | Tracks Triglavian/Pochven activity signals |
| Pochven Flashpoint Radar | Detects likely active flashpoint systems from kill bursts |
| ESS Raid Calculator | Estimates bank value, hack timing, and defender risk |
| Gank Efficiency Optimizer | Calculates attack cost, expected loot, and profitability |

---

# 🧱 Key Design Decisions

* Category-based navigation

  * keeps a growing toolset usable without a long flat tab list

* Paste-first workflows

  * users can bring in cargo, D-Scan, Local, ESS or market text directly from the game

* Wiki separated from calculators

  * static learning content does not interfere with data-driven tools

* Shared live-signal architecture

  * killmail-derived signals can support multiple frontend tools without duplicate polling

* Progressive expansion

  * new systems can be added while preserving the existing market dashboard

---

# 📈 Current Status

**Live Production Expansion**

* Wiki navigation is public
* OmniScanner is available on the start page
* Newer combat, Pochven and risk tools are integrated into category navigation
* Existing market, logistics and wormhole tools remain available

Used as part of:

https://eve-tradelooper.com/
