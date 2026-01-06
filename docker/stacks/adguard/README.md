# AdGuard Home

## Purpose
Network-wide DNS resolver with ad/tracker blocking and local DNS overrides. Which is to be improved with a new upcoming router

## Networking
- Runs on `lan_macvlan` with a LAN-native IP.
- No host port mappings required when using macvlan.

## Persistent data
- `${ADGUARD_CONF_DIR}` -> `/opt/adguardhome/conf`
- `${ADGUARD_WORK_DIR}` -> `/opt/adguardhome/work`

## Deploy
1. Copy `env.template` -> `.env` and update values:
   - set `ADGUARD_IPV4` to your macvlan LAN IP
   - confirm directory paths
2. Ensure the external Docker network `lan_macvlan` exists.
3. Deploy:

```bash
docker compose up -d

