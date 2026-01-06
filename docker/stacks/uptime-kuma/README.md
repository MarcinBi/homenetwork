# Uptime Kuma

## Purpose
Simple uptime monitoring and alerting for homelab services.

## Networking
- Runs on Docker bridge networking.
- Web UI exposed on TCP 3001.

## Persistent data
- `${KUMA_DATA_DIR}` -> `/app/data`

## Deploy
1. Copy `env.template` -> `.env` and set `KUMA_DATA_DIR`
2. Deploy:

```bash
docker compose up -d

