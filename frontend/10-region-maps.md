# Region Maps & Sovereignty

A DOTLAN-style region map system built directly from the real SDE galaxy coordinates, layered with live ESI activity and a capital-ship jump planner.

Unlike a static map image, every region is rendered as an interactive SVG from the actual in-game system coordinates, projected top-down and de-overlapped for label readability, then panned/zoomed and clicked like a real navigation tool.

---

# 🎯 Purpose

Give players a real navigation and intelligence surface for the map without needing DOTLAN, a login, or ads - built once from the SDE and kept current with hourly/20-minute ESI overlay refreshes instead of a static snapshot.

---

# 🛠️ Included Systems

| System | Purpose |
|---|---|
| Region maps | Per-region SVG rendered from real SDE coordinates, pan/zoom, click a system for a full dossier |
| Live overlays | Security, sovereignty, faction warfare, ship jumps/kills, NPC kills - 7 switchable modes |
| Open-all galaxy view | Renders all ~5,500 k-space systems as a single map, toggled on/off from the same button |
| Jump planner | Dijkstra route planning with exact light-year distances, editable ship/fuel presets, pick start/destination by clicking the map with highlighted jump-lane lines |
| Sovereignty Overview | Ranks nullsec-holding alliances by system count, jumps straight to an alliance's main region |
| System dossier | Neighbors, stations, trade-hub distances, active incursions, recent kills for any clicked system |

---

# 🧱 Key Design Decisions

* Real SDE coordinates, not a schematic layout

  * systems are projected from actual in-game x/y/z positions, so distances and layout match the real galaxy rather than an artistic approximation

* Region-hop navigation plus a full-galaxy escape hatch

  * DOTLAN's one-region-per-page model works well for detail, but you can only step to a neighboring region at a time; a second "Open all" view removes that limit when the big picture matters more than any one region

* No login required for any of it

  * the jump planner and sovereignty view work from public ESI endpoints only - no SSO, matching the platform-wide no-account policy

* Snapshot-based live overlays, not per-request ESI calls

  * jumps/kills/sovereignty/FW are refreshed on a schedule (hourly for combat activity, 20 minutes for sovereignty/FW, matching ESI's own cache windows) and served from the database, keeping the map fast regardless of ESI load

* Pointer-capture-safe click handling

  * a pan/zoom SVG surface needs `setPointerCapture()` for dragging, which silently retargets `pointerup`'s event target to the SVG itself on a real click - hit-testing had to move to `document.elementFromPoint()` instead of the usual `ev.target` pattern

---

# 📈 Current Status

**Live Production Feature**

* All k-space regions available individually and as one combined galaxy view
* Live overlay data refreshed on a schedule from public ESI
* Jump planner and sovereignty ranking fully functional without any account/login

Used as part of:

https://eve-tradelooper.com/
