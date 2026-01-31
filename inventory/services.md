# Services (Intent Only)

This file answers:
- What runs in the lab?
- What host runs it?
- How do users access it?
Without publishing internal addresses or credentials.

## Core infrastructure
### DNS filtering + local DNS overrides
Runs on: Debian server node  
Used for: ad blocking, local service names, stable internal access  
Access: LAN clients use it as primary DNS (via DHCP)

### Reverse proxy (TLS termination + routing + websockets)
Runs on: Debian server node  
Used for: friendly internal URLs, certificates, websocket support  
Access: internal-only; remote users connect via WireGuard then use the same URLs

## Apps
### Vaultwarden
Runs on: Debian server node  
Access: internal URL behind reverse proxy; remote access via WireGuard  
Notes: websockets enabled; internal DNS names may be used and are expected

### Monitoring
Runs on: Debian server node  
Includes: uptime monitoring + logs + dashboards  
Access: internal-only behind proxy

### Media server (Jellyfin)
Runs on: NAS  
Access:
- LAN: normal internal access
- Guest/IoT: allowed via a single explicit firewall exception to the Jellyfin service only

### Notes/sync (Joplin server + DB)
Runs on: NAS  
Access: internal URL behind proxy; remote via WireGuard
Notes: secrets not committed; compose templates are sanitized

## Trust model
- Trusted LAN: admin devices + homelab nodes
- Guest/IoT: isolated; only explicit exceptions allowed (e.g., Jellyfin)
