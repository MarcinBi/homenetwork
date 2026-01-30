# Updating NAS containers

## Safe default flow (per stack)
1. `docker compose pull`
2. `docker compose up -d`
3. Verify:
   - Jellyfin UI loads
   - Joplin UI/API loads
   - Logs are clean: `docker logs <container> --tail 200`

## Notes
- Jellyfin instances are `:latest` (linuxserver). Consider pinning to a major tag if you want stability.
- Joplin server is `:latest`. Same warning: convenient, but upgrades can surprise you.
