# Exposure model

## Not internet-exposed
Most services are internal-only and accessed via:
- internal DNS + reverse proxy
- WireGuard for remote access

## Internet-exposed
- WireGuard server (UDP) is intentionally exposed for remote access.
- Nothing else is intended to be directly exposed.
