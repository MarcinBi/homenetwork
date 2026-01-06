# Nginx Proxy Manager (NPM)

## Purpose
Reverse proxy used primarily for internal routing and TLS management.
Vaultwarden is exposed externally behind NPM.

## Networking
- Runs on `lan_macvlan` with a LAN-native IP.
- No host port mappings are required when using macvlan.

## Persistent data
- `/data` -> `${NPM_DATA_DIR}`
- `/etc/letsencrypt` -> `${NPM_LETSENCRYPT_DIR}`

## Deploy
1. Copy `env.template` -> `.env` and update values
2. Ensure the external Docker network `lan_macvlan` exists
3. Deploy:

```bash
docker compose up -d

