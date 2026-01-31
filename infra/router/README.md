# Router

Hardware: GLi.Net Flint 2 (OpenWrt-based)

This documentation is **intent-only** (public-safe). No IPs, keys, SSIDs, or hostnames.

## What it does
- Splits network into:
  - **Trusted LAN** (admin devices + servers)
  - **Guest/IoT** (TVs, smart devices, untrusted clients)
- Guest is isolated from LAN by default
- One explicit exception: Guest can reach the media service (Jellyfin) only
- Runs:
  - WireGuard **client** (Proton VPN) with policy routing
  - WireGuard **server** for remote access into the home network

See: `policies.md`
