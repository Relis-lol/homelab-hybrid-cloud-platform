# Future Hybrid Cloud Architecture

Planned architecture direction for optional cloud and public deployment experiments.

The local platform remains the primary system. Cloud services are only added where they provide clear operational value, such as monitoring, deployment validation, or optional backup experiments.

```mermaid
graph TD

%% ----------- USERS -----------
User["👤 Public User"]
Admin["💻 Admin Workstation"]

%% ----------- LOCAL SECURITY -----------
subgraph Security["Local Security Layer"]
    Firewall["🛡️ UFW Firewall"]
    Fail2Ban["🔒 Fail2Ban"]
end

%% ----------- FUTURE PUBLIC ACCESS -----------
subgraph PublicAccess["Future Public Access"]
    Proxy["🌐 Reverse Proxy"]
    HTTPS["🔐 HTTPS / TLS"]
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

%% ----------- OPTIONAL CLOUD SERVICES -----------
subgraph Cloud["☁️ Optional Cloud Services"]
    Monitor["📊 Azure Monitor / Metrics"]
    CI["🔁 GitHub Actions"]
    Storage["💾 Optional Archive Storage"]
end

%% ----------- CURRENT / PLANNED ACCESS -----------
Admin -->|SSH Key Auth| Firewall
Fail2Ban -.->|Protects SSH| Firewall
Firewall --> Local

User -.->|Future public access| HTTPS
HTTPS -.-> Proxy
Proxy -.-> Firewall

%% ----------- APPLICATION FLOW -----------
Frontend --> API
API --> DB

%% ----------- DATA INGESTION -----------
ESI --> Worker
Worker --> DB

%% ----------- OPTIONAL CLOUD CONNECTIONS -----------
Local -.->|Metrics / Logs| Monitor
CI -.->|Build / Validation / Deployment Workflow| Local
DB -.->|Optional Backup Experiment| Storage
```

## Notes

* Public access is planned, not required for local operation.
* Azure usage is optional and focused on monitoring experiments.
* Blob storage is treated as optional archive storage, not core infrastructure.
* The platform remains fully functional without cloud services.
