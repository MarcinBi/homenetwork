# Inventory

Public-safe inventory of the homelab: **intent and roles**, not literal network details.

## Included
- Host roles (router / server node / NAS)
- Services and where they run
- Access model (internal DNS + reverse proxy, VPN for remote access)
- Trust model (LAN vs Guest/IoT)

## Excluded (kept private)
- IP ranges, subnets, and exact host IPs
- MAC addresses and DHCP reservation tables
- Wi-Fi SSIDs and PSKs
- VPN keys and peer configs
- Real domain names if they map directly to internal services
- Secrets, `.env` values, resolved compose output containing passwords

