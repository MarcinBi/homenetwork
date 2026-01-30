# Jellyfin TikTok (short-form)

## What it is
A second Jellyfin instance pointed at a short-form media directory (/volume1/Sunder).

## IP / access
- Static IP (macvlan): 192.168.8.211
- Usually accessed via DNS hostname through reverse proxy.

## Data
- Config: /volume1/docker/tiktokFin/config
- Cache: /volume1/docker/tiktokFin/cache
- Media: /volume1/Sunder -> /data/tiktok

## Deploy/update
- `cd /volume1/docker/tiktokFin`
- `docker compose -f compose.yml pull`
- `docker compose -f compose.yml up -d`
