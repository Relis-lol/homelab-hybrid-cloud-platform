# Hybrid Cloud Architecture

Hybrid-cloud architecture for the EVE Trade Intelligence Platform.

The local platform remains the primary production system. Cloud services are used selectively for monitoring, visibility, and operational management.

```mermaid
graph TD

%% ----------- USERS -----------
User["👤 Public User"]
Admin["💻 Admin Workstation"]

%% ----------- PUBLIC EDGE -----------
Cloudflare["☁️ Cloudflare"]

%% ----------- LOCAL SECURITY -----------
subgraph Security["Local Security Layer"]
    Firewall["🛡️ UFW Firewall"]
    Fail2Ban["🔒 Fail2Ban"]
end

%% ----------- LOCAL PLATFORM -----------
subgraph Local["🖥️ Local Homelab Platform"]

    subgraph Docker["Docker Compose Stack"]
        Frontend["🌐 Frontend Dashboard"]
        API["⚙️ FastAPI Backend"]
        Worker["🔄 Market Worker"]
        DB[(🗄️ PostgreSQL)]
    end

end

%% ----------- EXTERNAL DATA -----------
ESI["📡 EVE ESI API"]

%% ----------- CLOUD MONITORING -----------
subgraph Azure["☁️ Azure Monitoring"]
    Arc["🔗 Azure Arc"]
    Monitor["📊 Azure Monitor"]
    Logs["📚 Log Analytics Workspace"]
end

%% ----------- LOCAL OBSERVABILITY -----------
subgraph Observability["Local Observability"]
    Discord["🔔 Discord Alerts"]
    CYD["📟 ESP32 CYD Display"]
end

%% ----------- PUBLIC ACCESS -----------
User --> Cloudflare
Cloudflare --> Frontend

%% ----------- ADMIN ACCESS -----------
Admin -->|SSH Key Auth| Firewall
Fail2Ban -.->|Protects SSH| Firewall
Firewall --> Local

%% ----------- APPLICATION FLOW -----------
Frontend --> API
API --> DB

%% ----------- DATA INGESTION -----------
ESI --> Worker
Worker --> DB

%% ----------- CLOUD MONITORING FLOW -----------
Local --> Arc
Arc --> Monitor
Monitor --> Logs

%% ----------- LOCAL OBSERVABILITY FLOW -----------
Local --> CYD
Worker --> Discord
Local --> Discord
```

## Notes

* Core workloads remain self-hosted.
* Azure is used for monitoring and hybrid visibility, not application hosting.
* PostgreSQL remains local and is not exposed publicly.
* Cloudflare handles public access, DNS, HTTPS, and edge protection.
* Discord and the ESP32 CYD display provide lightweight operational visibility.
