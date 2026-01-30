# Stack: dns (AdGuard Home)

## Purpose
Authoritative LAN DNS + filtering.

## Ports
- 53/tcp+udp (DNS)
- 3000/tcp (admin UI)
- 3002 -> 80/tcp (optional mapped port)

## Persistent data
- /srv/docker/adguard/work
- /srv/docker/adguard/conf

## Notes
Pin the image version (avoid `latest` surprises).
