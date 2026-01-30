# Sierrafin (Jellyfin main)

## IP / access
- Static IP (macvlan): 192.168.8.50
- Usually proxied via Debian Nginx (recommended)

## Media paths
- Movies: /volume1/Media/Movies -> /media/movies
- TV: /volume1/Media/Episodes -> /media/tv
- Music: /volume1/Media/Music -> /media/music

## Config paths
- /volume1/docker/sierrafin/config
- /volume1/docker/sierrafin/cache

## Deploy/update
- `cd /volume1/docker/sierrafin`
- `docker compose -f compose.yml pull`
- `docker compose -f compose.yml up -d`
