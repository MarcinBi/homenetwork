# Macvlan Network (lan_macvlan)

## Purpose
Some containers get real LAN IPs so they behave like first-class devices on the network.

## Config (current)
- Network: lan_macvlan
- Subnet: 192.168.8.0/24
- Gateway: 192.168.8.1
- Parent interface: eth0

## Assigned container IPs
- sierrafin: 192.168.8.50
- jellyfin_tiktok: 192.168.8.211

## Gotcha: host access
With macvlan, the NAS host may not be able to reach its own macvlan containers depending on setup.
If the NAS host needs to talk to these IPs, create a macvlan "shim" interface on the host bound to eth0 or access via
another machine on the LAN.
See ops/runbooks/macvlan-host-access.md
