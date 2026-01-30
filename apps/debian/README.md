# Debian Node (Prome)

This Debian server hosts the **control-plane** services for the homelab:

- DNS: AdGuard Home
- Edge / reverse proxy: Nginx Proxy Manager (NPM)
- Password manager: Vaultwarden (behind NPM)
- Monitoring: Uptime Kuma + Grafana/Loki/Promtail
- VPN: currently handled at router level (WireGuard on router). `/opt/stacks/vpn` exists for documentation/plans.

## Host filesystem layout (actual)
- `/opt/stacks/*` — compose + config for each stack
- `/srv/docker/*` — persistent container data
- `/srv/backups` — backups target

## Networking model
- Client DNS -> AdGuard -> internal hostnames
- Public/internal hostnames -> NPM (80/443)
- NPM forwards to containers via shared Docker network `proxy` (internal Docker DNS, e.g. `http://vaultwarden:80`)

## Ports (current)
- AdGuard UI: 3000/tcp
- DNS: 53/tcp+udp
- NPM: 80/81/443
- Uptime Kuma: 3001
- Grafana: 3010
- Loki: 3100

See:
- `stacks/*` for compose templates and per-stack notes
- `runtime/*` for bind mount mapping
- `ops/*` for update/runbooks
