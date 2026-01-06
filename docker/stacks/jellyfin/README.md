# Jellyfin

## Purpose
Self-hosted media server for LAN and VPN access.

## Access model
- Intended for LAN use and remote access via WireGuard (split tunnel).
- Not intended to be directly exposed to the internet.

## Networking
- Runs on `lan_macvlan` with a LAN-native IP.
- No host port mappings required when using macvlan.

## Persistent data
- `${JELLYFIN_CONFIG_DIR}` -> `/config`
- `${JELLYFIN_CACHE_DIR}` -> `/cache`
- `${JELLYFIN_MEDIA_DIR}` -> `/media` (read-only recommended)

## Deploy
1. Copy `env.template` -> `.env` and update:
   - `JELLYFIN_IPV4` to your macvlan LAN IP
   - directory paths if different
2. Ensure the external Docker network `lan_macvlan` exists.
3. Deploy:

```bash
docker compose up -d

