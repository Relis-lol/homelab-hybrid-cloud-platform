# 05 – Public Web Dashboard

## Objective

Provide a minimal public-facing interface for market data visualization.

---

## Core Features

- Read-only market data access
- Graph-based visualization
- Search / copy box functionality

---

## Visual Layer

Planned integration:

- Lightweight 3D sci-fi background (Spline)
- Isolated visual layer (no backend coupling)
- Lazy loading strategy
- Performance fallback for low-end devices

---

## Architecture Model

User → Reverse Proxy → API → Database

---

## Performance Considerations

- Frontend must not block API
- No heavy client-side computation
- Monitor load impact

---

## Current Status

Not yet implemented.

---

## Next Steps

- Define frontend framework
- Create layout mockup
- Integrate test API endpoint
