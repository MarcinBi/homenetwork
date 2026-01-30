# Stack: edge (Nginx Proxy Manager)

## Purpose
Reverse proxy for homelab hostnames.

## Ports
- 80/tcp, 443/tcp
- 81/tcp (NPM admin UI)

## Persistent data
- /srv/docker/npm/data
- /srv/docker/npm/letsencrypt

## Networking
NPM attaches to external network `proxy` so it can route to services like:
- `http://vaultwarden:80` (Docker DNS name inside the `proxy` network)

Keep the `proxy` network consistent.
