# Stack: monitoring

Includes:
- Uptime Kuma
- Loki
- Promtail
- Grafana

## Ports
- Uptime Kuma: 3001
- Grafana: 3010 -> 3000
- Loki: 3100

## Persistent data
- /srv/docker/uptime-kuma/data
- /srv/docker/monitoring/grafana
- /srv/docker/monitoring/loki
- /srv/docker/monitoring/promtail

## Config files
- Loki: `stacks/monitoring/logging/loki/config.yaml`
- Promtail: `stacks/monitoring/logging/promtail/config.yaml`
- Grafana provisioning datasource: `stacks/monitoring/logging/grafana/provisioning/datasources/config.yaml`

## Secrets
Move Grafana admin creds into `.env` and do NOT commit real values.
