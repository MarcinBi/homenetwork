# NAS Apps

This folder documents the application stacks running on the NAS host ("NASA").

DNS + reverse proxy live on a separate Debian server (AdGuard + Nginx). NAS services are exposed via that proxy.

## Running services (current)
- Joplin Server
  - Host port: 22300 (mapped to container 22300)
  - Base URL: proxied (see services/joplin)
  - DB: Postgres 16 (container `joplin-db`)
- Jellyfin (main media) "sierrafin"
  - Runs on macvlan with static LAN IP: 192.168.8.50
  - Media: /volume1/Media/{Movies,Episodes,Music}
- Jellyfin (short-form) "jellyfin_tiktok"
  - Runs on macvlan with static LAN IP: 192.168.8.211
  - Media: /volume1/Sunder

## Conventions
- Persistent container data lives under: /volume1/docker/<service>/
- Large media lives under: /volume1/Media and /volume1/Sunder
- Secrets are **never** committed. Use `.env.example` files and store real values in your secret manager/password manager.

## Quick commands (on NAS)
- View running containers:
  - `docker ps`
- Update a stack:
  - `docker compose pull && docker compose up -d`
- Export resolved compose (for audits):
  - `docker compose config`

See:
- storage/layout.md
- networks/macvlan.md
- ops/update.md
