``` mermaid

graph TD

    Internet((Internet))

    subgraph LAN["Home LAN 192.168.178.0/24"]
        Client["Admin Laptop"]
        Server["NiPoGi Mini Server"]
    end

    Internet -- blocked by firewall --> Server
    Client -->|SSH Key Auth| Server

    subgraph Docker["Docker Compose Stack"]
        API["FastAPI Container"]
        DB[(PostgreSQL Container)]
    end

    Server --> Docker
    API -->|internal docker network| DB

    Server -.->|log monitoring| Fail2Ban["Fail2Ban"]
    Fail2Ban -.->|ban brute force IPs| Block["IP Block"]
