# 05 – Public Web Dashboard

## Objective

Provide a public-facing interface for market analytics and tools.

---

## Core Features (Defined)

- Cargo value calculator (copy/paste input)
- Item search with autocomplete
- Market history graphs
- Read-only access to market data

---

## Architecture Model

User → Reverse Proxy → Frontend → API → Database

---

## UI Concept

- Lightweight frontend (React or similar)
- Optional 3D background layer (visual only)
- Fast loading, minimal dependencies
- Mobile-compatible layout

---

## Data Flow

- Frontend queries API endpoints
- No direct database access
- API handles all transformations

---

## Current Status

Backend fully prepared.

- API endpoints available
- Data pipeline operational
- Ready for frontend integration

---

## Next Steps

- Choose frontend framework
- Build cargo calculator UI
- Implement graph visualization
- Connect to API endpoints
