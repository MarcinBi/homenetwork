# Restore Runbook

This document outlines the high-level process for restoring the homelab after failure.

---

## Restore order

1. Verify NAS hardware and disks
2. Restore storage volumes
3. Bring up Docker
4. Restore reverse proxy (NPM)
5. Restore core services (DNS, VPN, Vaultwarden)
6. Restore application services (Jellyfin, monitoring)

---

## Notes

- persistent data lives outside the repository
- compose files are intended to be redeployed cleanly
- secrets are restored manually from secure storage

