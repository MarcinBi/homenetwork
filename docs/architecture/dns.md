# DNS Architecture

## Goal

The intended DNS design is to use **AdGuard Home** as a universal DNS resolver for the network, providing:

- ad and tracker blocking
- consistent internal name resolution
- centralized control over DNS behavior
- simplified access to services behind the reverse proxy

---

## Current state

DNS is **not currently functioning universally** across the network currently due to restrictions on the network's router.

### Symptoms
- clients continue using router-provided DNS
- internal hostnames do not resolve consistently
- DNS overrides are unreliable or ignored

### Root cause
- limitations or restrictions imposed by the current router
- inability to properly hand out custom DNS via DHCP

---

## Desired end state

- all LAN clients receive AdGuard Home as their primary DNS resolver
- internal DNS rewrites map service names to LAN IPs
- reverse proxy hostnames resolve cleanly
- optional upstream privacy features (DoH / DoT)

---

## Planned resolution paths

Possible solutions under consideration:

1. Configure router DHCP to explicitly advertise AdGuard Home as DNS
2. Disable router DHCP and move DHCP/DNS control to another device
3. Use a dedicated router/firewall appliance and demote the current router to AP/switch
4. Temporary per-device DNS configuration (non-ideal)

The chosen approach will be documented once implemented.

---

## Public documentation note

Exact domains and DNS records are intentionally omitted from this repository.
Examples use placeholder domains such as `example.com`.

