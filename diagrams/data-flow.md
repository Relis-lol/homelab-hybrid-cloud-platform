# Data Flow

```mermaid
graph TD

%% ----------- SOURCE -----------
ESI["📡 EVE Online ESI API"]

%% ----------- WORKER -----------
Worker["🔄 Market Worker"]
Validation["✅ Data Validation"]
Enrichment["🧩 Item & Translation Enrichment"]
Snapshots["📊 Regional Market Snapshots"]
History["📈 Historical Market Imports"]

%% ----------- DATABASE -----------
DB[(🗄️ PostgreSQL)]

%% ----------- API -----------
API["⚙️ FastAPI Backend"]

%% ----------- FRONTEND -----------
Dashboard["🌐 Dashboard Platform"]

%% ----------- MODULES -----------
Cargo["📦 Cargo Value"]
Charts["📈 Market Charts"]
TradeLooper["💹 Trade Looper"]
RouteRisk["🛡️ Hauling Intelligence"]
WHMapper["🕳️ Wormhole Mapping"]
News["📰 AHN News Network"]

%% ----------- OBSERVABILITY -----------
Runs["🧾 Import Run Tracking"]
Discord["🔔 Discord Notifications"]

%% ----------- USER -----------
User["👤 User"]

%% ----------- INGESTION FLOW -----------
ESI --> Worker
Worker --> Validation
Validation --> Enrichment
Enrichment --> History
Enrichment --> Snapshots

History --> DB
Snapshots --> DB
Worker --> Runs
Runs --> DB
Worker --> Discord

%% ----------- API FLOW -----------
DB --> API
API --> Dashboard

%% ----------- DASHBOARD MODULES -----------
Dashboard --> Cargo
Dashboard --> Charts
Dashboard --> TradeLooper
Dashboard --> RouteRisk
Dashboard --> WHMapper
Dashboard --> News

%% ----------- USER FLOW -----------
Dashboard --> User
