``` mermaid

graph TD
    Internet((Internet)) ---|Blocked by UFW| Server[NiPoGi Mini PC]
    subgraph Local_Network [Home LAN 192.168.178.0/24]
        Client[Dein Laptop] -->|SSH + Key| Server
        Server -->|Docker| API[API Container]
        API -->|Internal| DB[(PostgreSQL)]
    end
    Server -.->|Fail2Ban| Jail[Block Brute Force]
