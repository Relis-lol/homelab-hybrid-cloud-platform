# Trade Computer

A per-hub mispricing radar and inter-hub arbitrage screener across the five main trade hubs (Jita, Amarr, Dodixie, Hek, Rens), built entirely on the platform's own market database - no spreadsheet exports, no login, no character data.

---

# 🎯 Purpose

Surface the market opportunities traders otherwise dig out of Excel sheets by hand: mispriced listings, orders placed wrongly by other players, hubs starved of supply, and profitable haul-and-relist routes - each ranked and pre-filtered so the dashboard signposts the trade instead of dumping raw data.

---

# 🛠️ Included Systems

| System | Purpose |
|---|---|
| Instant profit | Sell orders sitting below the local buy wall - buy and flip to the buy order in one docking, net of sales tax |
| Underpriced sells | Listings far below the trusted 7-day average on liquid items - snipe candidates |
| Premium buy orders | Buy orders paying well above the weekly buy average - where to dump existing stock |
| Bargain buy walls | Items with real turnover whose top buy order is nearly zero - one small bid makes you top buyer |
| Supply gaps | Items a hub is starved of, with the cheapest source hub and net restock margin |
| Inter-hub arbitrage | Buy in the cheapest hub, haul, relist at the destination - net of tax and broker fees, ranked by realistic daily potential |

---

# 🧱 Key Design Decisions

* Server-side, not spreadsheet-side

  * the inspiration (community Excel trade computers fed by the EVE Excel add-in) requires per-user setup and refresh cycles; here one shared backend serves every visitor from the platform's existing 30-minute order-book snapshots

* Troll-listing-resistant averages

  * a weekly average built from the cheapest sell order is poisoned by a single absurd listing; every price-level comparison caps the average at 3x the buy-wall average, which also kills fantasy arbitrage margins toward destination hubs

* The right history table for the job

  * the platform keeps two history stores; the on-demand chart backfill covers only a few dozen types per region, while the snapshot-aggregated hub history covers ~5,300 - choosing the wrong one silently empties every deal list

* Fee-realistic profits

  * all margins are net: sales tax only when selling into buy orders, tax plus broker fee when relisting, using the same skill assumptions as the platform's Trade Looper

* No accounts, ever

  * the original tool reads character wallets and own orders via ESI login; this rebuild deliberately keeps the platform's no-login policy and limits itself to public market data

---

# 📈 Current Status

**Live Production Feature**

* All five hubs switchable in one dashboard, data refreshed from snapshots roughly every 30 minutes
* Click-to-copy item names for fast in-game market lookup
* Fully translated into the platform's seven languages

Used as part of:

https://eve-tradelooper.com/
