# Hybrid Cloud Architecture

Current production architecture combining a self-hosted platform with selected cloud services for monitoring, visibility, and operational management.

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
* PostgreSQL remains local and is not exposed publicly.
* Cloudflare provides DNS, HTTPS, and edge protection.
* Azure provides monitoring and hybrid-cloud management.
* Discord and CYD monitoring provide operational visibility.
* The platform remains operational even if cloud monitoring services are unavailable.
