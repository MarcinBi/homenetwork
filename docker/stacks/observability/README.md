# Observability (Grafana + Loki + Promtail)

## Purpose
Centralized dashboards (Grafana) and log aggregation (Loki) with Docker container log shipping (Promtail).

## Services
- **Loki**: log storage + query backend (exposes `:3100`)
- **Grafana**: dashboards UI (exposes `:3000`)
- **Promtail**: ships container logs to Loki (no exposed ports)

## Networking
- Runs on Docker bridge networking.
- Grafana is accessible at `http://<host>:3000`
- Loki is accessible at `http://<host>:3100` (typically internal-only)

## Persistent data
- Loki data: `${LOKI_DATA_DIR}` -> `/loki`
- Grafana data: `${GRAFANA_DATA_DIR}` -> `/var/lib/grafana`

## Config files
- Loki config: `${LOKI_CONFIG}` -> `/etc/loki/config.yml`
- Promtail config: `${PROMTAIL_CONFIG}` -> `/etc/promtail/config.yml`

## Credentials
Grafana admin credentials are configured via environment variables:
- `GRAFANA_ADMIN_USER`
- `GRAFANA_ADMIN_PASSWORD`

⚠️ Do not commit real credentials. Use `env.template` -> `.env`.

## Deploy
1. Copy `env.template` -> `.env` and set:
   - storage paths
   - Grafana admin credentials (use a strong password)
2. Ensure config files exist at the paths referenced by `LOKI_CONFIG` and `PROMTAIL_CONFIG`.
3. Deploy:

```bash
docker compose up -d

