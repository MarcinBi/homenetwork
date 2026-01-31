# 🧠 Home Network / Homelab

<p align="center">
  <img alt="homelab" src="https://img.shields.io/badge/homelab-documented-brightgreen">
  <img alt="docker" src="https://img.shields.io/badge/docker-compose-blue">
  <img alt="dns" src="https://img.shields.io/badge/dns-adblock%20%2B%20local%20records-purple">
  <img alt="reverse-proxy" src="https://img.shields.io/badge/reverse%20proxy-https%20everywhere-orange">
  <img alt="status" src="https://img.shields.io/badge/status-iterating-yellow">
</p>

A public, **sanitized** mirror of my home network + homelab setup.
The goal: documentation that’s *actually useful* when something breaks, when I rebuild, or when I move hardware.

> **No secrets. No real addressing. No internal hostnames.**
> Anything sensitive is represented as placeholders and intent.

---

## ✨ What’s in here

- **Router**: segmentation (trusted vs guest/IoT), VPN client + server, DHCP/DNS forwarding
- **DNS**: local records + adblocking via :contentReference[oaicite:2]{index=2}
- **Reverse proxy**: HTTPS termination + WebSockets via :contentReference[oaicite:3]{index=3}
- **Core services**:
  - Password manager: :contentReference[oaicite:4]{index=4}
  - Media: :contentReference[oaicite:5]{index=5} (standard library + “short-form library” instance)
  - Notes: :contentReference[oaicite:6]{index=6} server
  - Monitoring: :contentReference[oaicite:7]{index=7} + :contentReference[oaicite:8]{index=8} / :contentReference[oaicite:9]{index=9} / :contentReference[oaicite:10]{index=10}

- **Nodes**:
  - Router: :contentReference[oaicite:11]{index=11} (based on :contentReference[oaicite:12]{index=12} concepts)
  - “Debian server node”: :contentReference[oaicite:13]{index=13} (DNS / proxy / monitoring / passwords)
  - NAS node: storage + media + self-hosted apps

> Diagram + docs are meant to be “rebuild friendly”: if I wiped everything tomorrow, this repo should get me 80–90% of the way back.

---

## 🗺️ High-level architecture

```mermaid
flowchart TB
  internet((Internet))
  router[Router<br/>Segmentation + VPN]
  dns[DNS<br/>AdGuard Home]
  proxy[Reverse Proxy<br/>Nginx Proxy Manager]
  services[Internal Services<br/>Vaultwarden / Grafana / Uptime / etc.]
  nas[NAS Apps<br/>Jellyfin / Joplin / storage]
  clients[Clients<br/>Trusted + Guest/IoT]

  internet --> router
  router --> dns
  router --> clients
  dns --> proxy
  proxy --> services
  proxy --> nas

  clients --> dns
  clients --> proxy
