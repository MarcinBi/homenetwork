# Runtime paths (Debian)

## Stack definitions (compose lives here)
- /opt/stacks/dns
- /opt/stacks/edge
- /opt/stacks/monitoring
- /opt/stacks/passwords
- /opt/stacks/vpn

## Persistent Docker data (bind mounts)
- /srv/docker/adguard/{work,conf}
- /srv/docker/npm/{data,letsencrypt}
- /srv/docker/vaultwarden/data
- /srv/docker/uptime-kuma/data
- /srv/docker/monitoring/{grafana,loki,promtail}
- /srv/docker/wireguard/config
