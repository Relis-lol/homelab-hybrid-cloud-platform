# Wormhole Mapper

Lightweight browser-based wormhole mapping tool for EVE Online.
Built as a standalone portfolio project focused on clean UI, fast interaction, and zero backend dependency.

## Features

* Hex-based interactive wormhole map
* Create, edit, and connect systems visually
* Friendly / Neutral / Hostile standing system
* Wormhole connection tracking

  * Mass status
  * Ship size limits
  * Notes / labels
* Start-system highlighting
* Mouse-wheel zoom with smooth SVG rendering
* Local browser autosave
* Compressed export/import map codes
* Shareable map links
* Ctrl+V parsing for EVE Online text

  * Local chat route imports
  * Wormhole info parsing
* Ctrl+C formatted system summaries
* Fully client-side (no database or account required)

## Tech Stack

* HTML5
* CSS3
* Vanilla JavaScript
* SVG rendering
* LocalStorage
* Deflate/Base64 compressed exports

## Goal

The project was designed as a lightweight, responsive alternative to heavier EVE mapping tools while also serving as a frontend/UI engineering portfolio piece.

Focus areas included:

* interactive SVG systems
* data compression/export logic
* UX for dense information maps
* clean browser-only architecture
* real-world usability for EVE wormhole players
