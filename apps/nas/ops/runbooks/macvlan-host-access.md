# Macvlan host ↔ container access issue

## Symptom
NAS host cannot reach macvlan container IPs (but other LAN devices can).

## Why
macvlan commonly isolates host from macvlan endpoints unless you add a host-side macvlan interface.

## Fix (example approach)
Create a macvlan shim on the host bound to eth0 and add a route.
Implementation differs by NAS OS/vendor. Document the exact commands you used once confirmed.
