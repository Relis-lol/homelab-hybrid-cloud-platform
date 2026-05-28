# Wormhole Mapping System

Browser-based wormhole mapping and route visualization tool for EVE Online.

Built as a standalone frontend application focused on interactive graph visualization, compressed data sharing, and real-time map editing without backend dependencies.

---

# 🖼️ Preview

![WH Mapper](../assets/wh-mapper.png)

---

# 🎯 Purpose

Provide a fast and lightweight way to build, maintain, and share wormhole chain maps.

---

# 🛠️ Core Features

| Area           | Features                                |
| -------------- | --------------------------------------- |
| Mapping        | Interactive system creation and editing |
| Visualization  | Zoomable SVG-based map rendering        |
| Connections    | Wormhole link management                |
| Classification | Friendly, Neutral, and Hostile systems  |
| Tracking       | Mass status and ship-size restrictions  |
| Notes          | Labels and custom annotations           |
| Sharing        | Export and import map codes             |
| Parsing        | EVE text import support                 |
| Persistence    | Automatic browser storage               |

---

# 🧱 Key Design Decisions

* Fully client-side architecture

  * no backend or database required

* SVG rendering instead of canvas

  * scalable graphics and lightweight interaction

* Compressed export format

  * easy sharing of large maps

* Browser persistence

  * maps survive page refreshes and sessions

* Designed for dense information layouts

  * remains usable with large wormhole chains

---

# 📊 Mapping Capabilities

### System Management

* Create systems
* Edit systems
* Delete systems
* Highlight start systems
* Assign standing categories

### Wormhole Connections

* Create links
* Track mass status
* Track ship-size restrictions
* Add notes and labels
* Visual route organization

---

# 🔄 Data Sharing

Supported workflows:

```text id="3km5hd"
Create Map
    ↓
Compress Data
    ↓
Generate Share Code
    ↓
Import on Another Browser
    ↓
Restore Full Layout
```

---

# 📋 EVE Integration

Supported clipboard workflows:

* Ctrl+V route imports
* Wormhole information parsing
* Local chat route extraction
* Ctrl+C formatted system summaries

---

# ⚙️ Tech Stack

* HTML5
* CSS3
* Vanilla JavaScript
* SVG Rendering
* LocalStorage
* Deflate Compression
* Base64 Encoding

---

# 📈 Current Status

**Operational**

* Interactive system editor
* Wormhole connection tracking
* SVG map rendering
* Zoom controls
* Browser autosave
* Export/import system
* Shareable map codes
* Clipboard integration

---

# 🔮 Future Expansion

* Advanced route analysis
* Chain statistics
* Automated route validation
* Connection lifetime tracking
* Fleet planning overlays
* Additional visualization layers
