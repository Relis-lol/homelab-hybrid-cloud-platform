# Credits & Compliance

Credits, contact information, and legal notices for EVE TradeLooper.

---

# 🎯 Purpose

Provide transparent attribution, project contact information, and required legal disclosures while keeping the platform lightweight and privacy-friendly.

---

# 🛠️ Included Components

| Component           | Purpose                               |
| ------------------- | ------------------------------------- |
| Contact Information | Ingame and project contact options    |
| Credits Section     | Project attribution                   |
| CCP Disclaimer      | Intellectual property acknowledgement |
| AI Disclosure       | Generated content transparency        |
| Compliance Design   | Privacy-focused platform structure    |

---

# 🧱 Design Decisions

* Minimal contact footprint

  * project contact available without exposing unnecessary personal information

* No user accounts

  * tools can be used without registration or identity tracking

* Data minimization

  * no account database, login system, or user profiling
  * voluntary contact and Wiki submissions are processed only for the requested interaction and moderation

* Legal information separated from gameplay tools

  * keeps the main interface focused and uncluttered

* CCP rights clearly acknowledged

  * the published CCP rights notice is reproduced in its required wording

* Public data sources only

  * market information is sourced from publicly available ESI endpoints

* AI-generated content disclosed

  * improves transparency for generated summaries and news content

---

# ⚖️ Legal Disclaimer

© 2014 CCP hf. All rights reserved. "EVE", "EVE Online", "CCP", and all related logos and images are trademarks or registered trademarks of CCP hf.

This application has been created under the EVE Developer License Agreement.

This is an unofficial fan-made project and is not affiliated with, endorsed by, or connected to Fenris Creations (formerly CCP Games).

Market prices, cargo estimates, route calculations, trade suggestions, safety ratings and other generated information may be delayed, incomplete or inaccurate. Use at your own risk.

Parts of this project use publicly available EVE Online ESI API data.

News headlines, summaries and atmospheric roleplay-style text may be automatically generated or rewritten by AI systems for entertainment and immersion purposes. Original sources and copyrights remain with their respective owners.

---

# 🔒 Privacy Approach

The platform is intentionally designed to minimize personal data handling.

* No user accounts
* No registration requirements
* No profile system
* No gameplay tracking

The core tools can be used without creating an account or submitting personal
information. The following optional features process user-provided data:

* Contact submissions can contain a message, optional name and email address,
  and an optional image. The sender IP address is stored for anti-spam and
  per-sender rate limiting.
* Wiki submissions can contain an article title and text, an optional in-game
  character name, and optional images. The sender IP address is stored for
  anti-spam and per-sender rate limiting.
* Contact and Wiki submissions enter protected moderation queues. Wiki content
  is reviewed manually and is never published automatically.
* Operational visitor counts use day-scoped salted hashes so visitors cannot
  be recognized across different days.

No fixed retention period is claimed here; storage and deletion rules should
be reviewed as part of the platform's operational data-retention policy.

---

# 📈 Current Status

**Live Production Deployment**

* Contact information available
* Credits section
* CCP disclaimer
* AI disclosure
* Privacy-focused design
* Dashboard integration

Used as part of:

https://eve-tradelooper.com/
