``` mermaid
graph LR

%% ---------- USERS ----------
User["Public User / Browser"]
Admin["Admin Laptop"]
EVE["EVE Online Market API"]

%% ---------- SERVER ----------
subgraph Server["NiPoGi Mini Server (Ubuntu)"]

    subgraph Security["Security Layer"]
        UFW["UFW Firewall"]
        Fail2Ban["Fail2Ban"]
    end

    subgraph Docker["Docker Compose Stack"]
        Web["EVE Market Website"]
        API["FastAPI Service"]
        Worker["Market Import Worker"]
        DB[(PostgreSQL History Database)]
    end

end

%% ---------- AZURE ----------
subgraph Azure["Azure Cloud"]
    CI["CI/CD Automation"]
    Storage["Cloud Storage / Backup"]
end


%% ---------- ACCESS ----------
User -->|HTTPS| UFW
Admin -->|SSH Key Auth| UFW
UFW --> Web

Fail2Ban -.->|protects SSH| UFW

%% ---------- APPLICATION FLOW ----------
Web --> API
API --> DB

%% ---------- DATA PIPELINE ----------
EVE -->|market data| Worker
Worker -->|store history| DB

%% ---------- CLOUD INTEGRATION ----------
CI -->|deploy / update| Web
DB -.->|backup / sync| Storage
