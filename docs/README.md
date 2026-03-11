``` mermaid

graph TD

    User["Public User / Browser"]
    Admin["Admin Laptop"]

    subgraph LAN["Home LAN / Secure Admin Access"]
        Server["NiPoGi Mini Server"]
        Fail2Ban["Fail2Ban"]
        UFW["UFW Firewall"]
    end

    Admin -->|SSH Key Auth| Server
    UFW --> Server
    Fail2Ban -.->|protects SSH| Server

    subgraph Docker["Docker Compose Stack on Server"]
        Web["EVE Market Website"]
        API["FastAPI Service"]
        Worker["EVE Data Import Worker"]
        DB[(PostgreSQL History Database)]
    end

    User -->|HTTPS / Web Access| Web
    Web -->|API Requests| API
    API -->|Read / Query| DB
    Worker -->|Import / Update Market Data| DB

    EVE["EVE Online Market Data"] -->|Fetch Data| Worker

    Server --> Docker

    subgraph Azure["Azure Integration"]
        Blob["Storage / Backup / Future Services"]
        CI["CI/CD / Automation"]
    end

    Docker --> Azure
    CI --> Docker
    DB -.->|backup / sync| Blob
