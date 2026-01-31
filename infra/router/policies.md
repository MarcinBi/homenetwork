# Router policies (intent)

## Networks
- **Trusted LAN**: full internal access + internal DNS
- **Guest/IoT**: client isolation, no LAN access by default, internet allowed

## DHCP
- Router provides DHCP for both networks
- Infrastructure hosts use stable addressing (static/reserved), but the repo does not list them
- LAN DHCP hands out internal DNS as primary resolver (optional public fallback)
- Guest DHCP uses either public DNS or forced internal DNS depending on leak-prevention preference

## DNS
- LAN uses an internal DNS/filtering stack with local overrides
- Guest cannot bypass DNS policy (enforced via firewall where desired)

## Firewall
Default:
- LAN → WAN: allow
- Guest → WAN: allow
- Guest → LAN: deny

Exception:
- Guest → Jellyfin: allow only the required TCP port to the media service endpoint
- Everything else Guest → LAN remains blocked

## VPN policy routing
- Some traffic is routed over the WireGuard VPN client tunnel
- Marking + separate routing table selects VPN vs direct WAN
- Leak protection blocks VPN-marked traffic if the tunnel is down

## Port forwards
- Avoid exposing internal services publicly
- Only intentional WAN exposure: WireGuard server UDP (for remote access)
