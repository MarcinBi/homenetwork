# Homelab

Personal homelab documentation and infrastructure templates for a self-hosted home network.

This repository documents the architecture, networking decisions, and services running in my home lab.  
It is documentation-first and intentionally public-safe — no secrets, credentials, or sensitive identifiers are committed.

---

## Overview

This homelab is centered around a NAS-based Docker host with supporting client machines.  
The primary goals are:

- reliable self-hosted services
- clean internal networking
- secure remote access
- clear documentation for rebuilds, expansion, and troubleshooting

---

## Core Components

### Hosts
- **UGreen DXP2800 (NAS)**  
  Primary storage and Docker host for all services.

- **Arch Linux workstation**  
  Administration, development, and homelab management.

### Networking
- **Reverse proxy:** Nginx Proxy Manager  
  Used primarily for internal routing; select services are internet-facing.
- **VPN:** WireGuard (split tunnel)  
  Secure remote access to internal services.
- **DNS:** AdGuard Home (planned universal DNS)  
  Currently under migration due to router limitations.
- **Container networking:**  
  - macvlan for LAN-native services  
  - bridge for internal-only services

### Services (current)
- Nginx Proxy Manager
- Jellyfin
- Vaultwarden (internet-facing)
- AdGuard Home
- WireGuard (wg-easy)
- Uptime Kuma
- Grafana / Loki / Promtail (work in progress)

---

## Repository Structure

```text
.
├── docs/           # Architecture, networking, and runbooks
├── inventory/      # Hardware and host inventory
├── docker/         # Docker stacks and service documentation
├── networking/     # Network-specific deep dives (macvlan, DNS, VPN)
├── plans/          # Roadmap, known issues, and future work
└── README.md

