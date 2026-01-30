# Stack: passwords (Vaultwarden)

## Purpose
Self-hosted Bitwarden-compatible server.

## Access model
- Public/internal hostname: https://vault.sierra-117.net
- Routed via Nginx Proxy Manager.
- NPM forwards to `http://vaultwarden:80` on shared Docker network `proxy`.

## Persistent data
- /srv/docker/vaultwarden/data

## Notes
- Websockets should be enabled in NPM for stable clients.
- Keep `DOMAIN` consistent with the URL used in clients.
