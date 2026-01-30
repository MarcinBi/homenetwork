# Permissions

## Jellyfin containers
- sierrafin runs with:
  - PUID=1000
  - PGID=10
- jellyfin_tiktok runs with:
  - PUID=1000
  - PGID=1000

If you see library scanning issues or "permission denied", confirm ownership and group
permissions on:
- /volume1/Media
- /volume1/Sunder
- /volume1/docker/sierrafin/*
- /volume1/docker/tiktokFin/*

Recommended checks:
- `ls -la /volume1/Media`
- `ls -la /volume1/Sunder`
