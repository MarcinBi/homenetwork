# Architecture Overview

## What this homelab is optimizing for
- **Simple, reliable self-hosting** (NAS as the primary Docker host)
- **Clean internal access** via reverse proxy + DNS
- **Secure remote access** via WireGuard (split tunnel)
- **Documentation-first** workflows so the stack is rebuildable and extensible

---

## Hosts

### UGreen DXP2800 (NAS)
- Acts as the **single Docker host** today
- Stores persistent volumes and application data
- Runs core services (reverse proxy, DNS, VPN, secrets, media)

### Arch Linux workstation
- Used for:
  - managing/maintaining the homelab
  - authoring configs/docs
  - future tooling and automation work

---

## Core networking design

### Reverse proxy (Nginx Proxy Manager)
- Primary purpose: **internal reverse proxying** for services
- Secondary purpose: expose select services externally
  - **Vaultwarden is internet-facing** behind the reverse proxy

### VPN (WireGuard via wg-easy)
- **Split tunnel**
- Used for secure remote access to internal services (example: Jellyfin)

### DNS (AdGuard Home)
- Target end state: **universal DNS** for the LAN (all clients use AdGuard)
- Current state: **not working universally** due to router constraints
- Planned: migrate DHCP/DNS control away from the router if required

---

## Container networking strategy

Two modes are used:

### macvlan (LAN-native container IPs)
Used for:
- Nginx Proxy Manager (`npm`)
- Jellyfin
- AdGuard Home
- Vaultwarden

Reasoning:
- these services benefit from being first-class “LAN devices”
- avoids port conflicts on the host
- simplifies access patterns from LAN clients

### bridge (default Docker networking)
Used for:
- wg-easy (WireGuard management)
- Uptime Kuma
- Grafana / Loki / Promtail (work in progress)

---

## Services (current)

### Access / Networking
- Nginx Proxy Manager (reverse proxy)
- WireGuard (wg-easy)
- AdGuard Home (DNS / filtering)

### Apps
- Vaultwarden (password manager; internet-facing via NPM)
- Jellyfin (media; LAN + VPN)
- Uptime Kuma (availability monitoring)

### Observability (WIP)
- Grafana
- Loki
- Promtail

---

## Known gaps (tracked in /plans)
- DNS not universal due to router limitations
- Observability stack not finalized (Grafana/Loki/Promtail)
- Compose files and templates will be added incrementally once sanitized

