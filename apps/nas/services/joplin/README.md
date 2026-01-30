# Joplin Server

## What it is
Self-hosted Joplin server with Postgres backend.

## Network exposure
- Container port: 22300
- Host port: 22300
- Intended access: via reverse proxy on Debian server
  - APP_BASE_URL should match the public/internal hostname (https)

## Data paths (NAS)
- Postgres data: /volume1/docker/joplin/data/postgres

## Deploy/update (on NAS)
- `cd /volume1/docker/joplin`
- `docker compose pull`
- `docker compose up -d`

## Notes
- Secrets are provided via environment variables. Do not commit real values.
