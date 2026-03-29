# 04 – API Layer

## Objective
Provide a controlled application layer between the database and external consumers.
The API handles structured data access, query logic, and business-level transformations.

---

## Technology Stack
- **Language:** Python FastAPI
- **Deployment:** Docker container
- **Server:** Uvicorn ASGI
- **Database:** PostgreSQL via `psycopg`

---

## Architecture Concept
`Client` → `API` → `PostgreSQL`

---

## Responsibilities
- Request validation
- Data aggregation and transformation
- Controlled database access
- JSON response formatting

---

## Current Capabilities
The API has moved beyond test endpoints and now exposes real application functionality.

### Core Features
- Item lookup and search
- Global price retrieval (ESI)
- Regional market history access
- Cargo value calculation (multi-item input)
- Import run tracking

---

## Available Endpoints


| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/health` | Service health check. |
| `GET` | `/db-check` | Database connectivity validation. |
| `GET` | `/items` | Returns item metadata. |
| `GET` | `/items/search?q=...` | Case-insensitive item search. |
| `GET` | `/esi/global-prices` | Returns current global price data. |
| `GET` | `/market-history?type_id=...&region_id=...` | Returns historical market data. |
| `POST` | `/cargo/value` | Calculates total cargo value based on item list input. |
| `GET` | `/import-runs` | Returns import execution history. |

---

## Business Logic Layer
Die API übernimmt komplexe Aufgaben wie:
- **JOIN-Operationen** zwischen Item-Metadaten und Preistabellen.
- **Aggregation** von Multi-Item-Frachtwerten.
- **Filterung** historischer Marktdaten nach Region und Typ.

---

## Security Model
- Keine direkte Datenbank-Exposition nach außen.
- Kontrollierte Abfrage-Oberfläche (Query Surface).
- Input-Validierung durch FastAPI.
- Zugriffsbeschränkung über Firewall (LAN-restricted).

---

## Current Status
-  Voll einsatzbereiter Application Layer.
-  An echte Marktdaten angebunden.
-  Multi-Endpoint-Struktur aktiv.
-  Integration der Worker-Prozesse bestätigt.

---

## Known Limitations & Next Steps

### Limitations
- Keine Authentifizierung oder Rate Limiting.
- Fehlende Paginierung bei großen Datenmengen.
- Pydantic-Modelle (Response Schemas) noch unvollständig.
- Kein Caching-Layer (z. B. Redis).

### Next Steps
-  Response-Modelle vervollständigen.
-  Paginierung und Filterung für Markt-Queries einführen.
-  Caching-Layer implementieren.
-  Trennung von Test- und Produktions-Endpunkten.
-  API-Design für Frontend-Konsum optimieren.

