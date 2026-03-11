``` mermaid

graph TD

%% ---------- INTERNET ----------
User["Public User / Browser"]
Admin["Admin Laptop"]
EVE["EVE Online Market API"]

%% ---------- SECURITY ----------
subgraph Security["Server Security"]
    UFW["UFW Firewall"]
    Fail2Ban["Fail2Ban"]
end

%% ---------- SERVER ----------
Server["NiPoGi Mini Server (Ubuntu + Docker)"]

%% ---------- APPLICATION ----------
subgraph Application["Docker Compose Stack"]
    Web["EVE Market Website"]
    API["FastAPI Service"]
    Worker["Market Import Worker"]
end

%% ---------- DATA ----------
DB[(PostgreSQL History Database)]

%% ---------- CLOUD ----------
subgraph Azure["Azure Cloud Integration"]
    CI["CI/CD Automation"]
    Storage["Cloud Backup / Storage"]
end

%% ---------- ACCESS ----------
User -->|HTTPS| UFW
Admin -->|SSH Key Auth| UFW
UFW --> Server
Fail2Ban -.->|Protects SSH| UFW

%% ---------- SERVICES ----------
Server --> Web
Web --> API
API --> DB

%% ---------- DATA IMPORT ----------
EVE -->|Market Data| Worker
Worker -->|Store History| DB

%% ---------- CLOUD ----------
CI -->|Deploy / Update| Server
DB -.->|Backup / Sync| Storage
