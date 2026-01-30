# Updating stacks (Debian)

Typical per-stack flow (run on the Debian server):

1) `cd /opt/stacks/<stack>`
2) `docker compose pull`
3) `docker compose up -d`
4) Verify with:
   - `docker ps`
   - `docker logs <container> --tail 200`

Notes:
- Prefer **pinned versions** over `:latest` for DNS/proxy.
- Keep the shared external Docker network `proxy` intact (NPM + Vaultwarden rely on it).
