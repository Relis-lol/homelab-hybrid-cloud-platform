```mermaid

graph TD

%% ----------- ADMIN / USER -----------
Admin["Admin Laptop"]
User["Public User / Browser"]
EVE["EVE Online Market API"]

%% ----------- SECURITY -----------
subgraph Security["Server Security"]
    UFW["UFW Firewall"]
    Fail2Ban["Fail2Ban"]
end

%% ----------- SERVER -----------
Server["NiPoGi Mini Server (Ubuntu + Docker)"]

%% ----------- APPLICATION -----------
subgraph Docker["Docker Compose Stack"]

    Web["🌐 EVE Market Website (Public Interface)"]

    API["FastAPI Service"]

    Worker["Market Import Worker"]

end

%% ----------- DATABASE -----------
DB[(PostgreSQL History Database)]

%% ----------- AZURE -----------
subgraph Azure["Azure Cloud"]
    CI["CI/CD Automation"]
    Storage["Backup / Storage"]
end

%% ----------- ACCESS -----------
Admin -->|SSH Key Auth| UFW
User -->|HTTPS| UFW

Fail2Ban -.->|Protects SSH| UFW
UFW --> Server

%% ----------- SERVER FLOW -----------
Server --> Web
Web --> API
API --> DB

%% ----------- DATA IMPORT -----------
EVE -->|Market Data| Worker
Worker -->|Store History| DB

%% ----------- CLOUD -----------
CI -->|Deploy / Update| Server
DB -.->|Backup / Sync| Storage
