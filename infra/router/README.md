
# Router

Hardware: :contentReference[oaicite:0]{index=0}  
Firmware family: OpenWrt-based (GL.iNet)

This folder documents router configuration at an **intent / design** level.
No secrets or identifying network details are stored here.

## Goals
- Segment the network into:
  - **Trusted LAN** (admin devices + homelab nodes)
  - **Guest / IoT** (smart TVs, untrusted clients)
- Keep Guest isolated from LAN by default
- Allow **a single, explicit exception** for media access (Guest → Jellyfin)
- Run outbound VPN client (WireGuard, Proton) with policy routing
- Run inbound WireGuard server for remote access into the home network

## What is intentionally excluded
- Real IP ranges / internal IPs
- SSIDs, Wi-Fi passwords
- MAC addresses / DHCP reservation tables
- WireGuard keys and peer details
- Full firewall exports
