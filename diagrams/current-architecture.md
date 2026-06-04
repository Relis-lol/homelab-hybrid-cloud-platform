## Current Platform Architecture

```mermaid
graph TD

%% ----------- USERS -----------
User["👤 Public User"]
Admin["💻 Admin Workstation"]

%% ----------- CLOUDFLARE -----------
CF["☁️ Cloudflare"]

%% ----------- SECURITY -----------
subgraph Security["Host Security"]
    UFW["🛡️ UFW Firewall"]
    Fail2Ban["🔒 Fail2Ban"]
end

%% ----------- HOST -----------
Server["🖥️ Ubuntu Server"]

%% ----------- DOCKER -----------
subgraph Docker["Docker Compose Stack"]

    Frontend["🌐 Dashboard Platform"]

    API["⚙️ FastAPI Backend"]

    Worker["🔄 Market Worker"]

    DB[(🗄️ PostgreSQL)]

end

%% ----------- OBSERVABILITY -----------
subgraph Monitoring["Observability"]

    Azure["☁️ Azure Monitor / Arc"]

    Discord["🔔 Discord Alerts"]

    CYD["📟 ESP32 CYD Display"]

end

%% ----------- EXTERNAL -----------
ESI["📡 EVE ESI API"]

%% ----------- PUBLIC ACCESS -----------
User --> CF
CF --> Frontend

%% ----------- ADMIN ACCESS -----------
Admin -->|SSH Key Auth| UFW
Fail2Ban -.->|Protects SSH| UFW
UFW --> Server

%% ----------- APPLICATION FLOW -----------
Server --> Frontend
Frontend --> API
API --> DB

%% ----------- DATA PIPELINE -----------
ESI --> Worker
Worker --> DB

%% ----------- ANALYTICS FLOW -----------
DB --> API
API --> Frontend

%% ----------- OBSERVABILITY FLOW -----------
Server --> Azure
Server --> Discord
Server --> CYD
Worker --> Discord
```
