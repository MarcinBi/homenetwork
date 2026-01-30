# Runbook: Vaultwarden intermittent client "network" issues

Common cause: reverse proxy websocket handling.

In Nginx Proxy Manager (Proxy Host for Vaultwarden):
- Websockets Support: ON
- Advanced: keep minimal, usually just timeouts:
  - `proxy_read_timeout 3600s;`
  - `proxy_send_timeout 3600s;`

If you add "Advanced" config and the host breaks:
- Validate NPM nginx config:
  - `docker exec -it nginx-proxy-manager nginx -t`
- Check logs:
  - `docker logs --tail 200 nginx-proxy-manager`

Upstream should be:
- scheme: http
- host: `vaultwarden`
- port: 80
