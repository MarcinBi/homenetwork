
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
- **DNS**: local records + adblocking via AdGuard Home
- **Reverse proxy**: HTTPS termination + WebSockets via Nginx Proxy Manager
- **Core services**:
  - Password manager: Vaultwarden
  - Media: Jellyfin (standard library + “short-form library” instance)
  - Notes: Joplin server
  - Monitoring: Uptime Kuma + Grafana / Loki / Promtail

- **Nodes**:
  - Router: GL.iNet Flint 2 (OpenWrt-style config concepts)
  - Debian server node: DNS / proxy / monitoring / passwords
  - NAS node: storage + media + self-hosted apps

This repo is meant to be “rebuild friendly”: if everything got wiped tomorrow, it should get me 80–90% of the way back without guessing.

---

## 🗺️ High-level architecture

```mermaid
flowchart TB
  internet((Internet))
  router[Router<br/>Segmentation + VPN]
  dns[DNS<br/>AdGuard Home]
  proxy[Reverse Proxy<br/>Nginx Proxy Manager]
  services[Internal Services<br/>Vaultwarden / Monitoring / Etc.]
  nas[NAS Apps<br/>Jellyfin / Joplin / Storage]
  clients[Clients<br/>Trusted + Guest/IoT]

  internet --> router
  router --> dns
  router --> clients

  clients --> dns
  clients --> proxy

  dns --> proxy
  proxy --> services
  proxy --> nas
