# Vaultwarden

## Purpose
Self-hosted password manager (Bitwarden-compatible).

## Access model
- Vaultwarden is **internet-facing**, published through **Nginx Proxy Manager**.
- Recommended: HTTPS-only and keep the admin page restricted.

## Networking
- Runs on `lan_macvlan` with a LAN-native IP.
- No host port mappings required when using macvlan.

## Persistent data
- `/data` -> `${VW_DATA_DIR}`

## Deploy
1. Copy `env.template` -> `.env` and fill in real values:
   - set `ADMIN_TOKEN` (strong secret; do not commit)
   - set `VW_IPV4` to your macvlan LAN IP
2. Ensure the external Docker network `lan_macvlan` exists.
3. Deploy:

```bash
docker compose up -d

