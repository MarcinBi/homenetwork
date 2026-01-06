# wg-easy (WireGuard)

## Purpose
Simple WireGuard VPN management with a web UI.

## Access model
- VPN traffic: UDP 51820
- Admin UI: TCP 51821
- Used as a **split tunnel** for accessing internal services (e.g. Jellyfin)

## Networking
- Uses Docker bridge networking
- Requires host port mappings

## Persistent data
- `${WG_DATA_DIR}` -> `/etc/wireguard`

## Deploy
1. Copy `env.template` -> `.env`
2. Set:
   - `WG_HOST` (public hostname or IP)
   - `PASSWORD_HASH`
3. Deploy:

```bash
docker compose up -d

