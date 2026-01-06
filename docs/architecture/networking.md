# Networking Architecture

This document describes how networking is handled across the homelab, including container networking modes, routing decisions, and access patterns.

---

## High-level approach

The homelab prioritizes:
- simplicity over premature complexity
- LAN-native access where it makes sense
- minimal port conflicts
- clear separation between internal-only and externally reachable services

All containers currently run on the NAS.

---

## Container networking modes

Two Docker networking modes are used intentionally.

---

### macvlan (LAN-native containers)

macvlan is used for services that benefit from behaving like independent devices on the LAN.

**Containers using macvlan:**
- Nginx Proxy Manager (`npm`)
- Jellyfin
- AdGuard Home
- Vaultwarden

**Why macvlan is used here:**
- each service gets its own LAN IP
- avoids port collisions on the NAS host
- simplifies firewall rules and client access
- services can be referenced directly or via DNS without NAT tricks

**Known macvlan caveat:**
- the Docker host (NAS) cannot easily communicate with macvlan containers without additional routing
- this is currently acceptable and documented for future mitigation if needed

---

### bridge (default Docker networking)

The default Docker bridge is used for services that:
- do not need direct LAN exposure
- are accessed internally or via another service (reverse proxy, VPN)
- are still under development or experimentation

**Containers using bridge networking:**
- wg-easy (WireGuard management)
- Uptime Kuma
- Grafana (WIP)
- Loki (WIP)
- Promtail (WIP)

---

## Reverse proxy usage (Nginx Proxy Manager)

Nginx Proxy Manager serves two roles:

### Internal routing
- provides friendly hostnames for internal services
- centralizes TLS and routing logic
- simplifies client access patterns

### External exposure
- Vaultwarden is exposed to the internet through NPM
- other services are intentionally kept internal and accessed via VPN

---

## VPN (WireGuard)

- managed via **wg-easy**
- configured as a **split tunnel**
- remote devices gain access to internal services (e.g. Jellyfin) without routing all traffic through the home network

---

## Future improvements
- document host ↔ macvlan communication options
- formalize firewall rules once DNS is stabilized
- revisit network segmentation if additional hosts are added

