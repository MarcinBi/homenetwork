# Hardware Inventory

## NAS (Primary Host)

- **Model:** UGreen DXP2800
- **Role:** Primary storage + Docker host (all containers currently run here)
- **CPU:** Intel N100 (4C/4T)
- **Memory:** 8 GB (reported 5600 MT/s)
- **Network:** 1 Gbps LAN

### Storage
- **Pool 1:** Basic (single disk) — Seagate ~7.28 TB  
  - **Volume 1:** ~7.20 TB total, ~0.62 TB used
- **Pool 2:** Basic (single disk) — Western Digital ~9.10 TB  
  - **Volume 2:** ~9.01 TB total, ~0.00 TB used

> Note: Pool type is currently “Basic” per-disk. Future improvement may include redundancy (e.g., RAID1/RAIDZ) depending on hardware goals.

---

## Workstation / Admin PC

- **OS:** Arch Linux (rolling)
- **Kernel:** 6.17.9-arch1-1
- **Role:** Homelab administration + development workstation
- **Architecture:** x86_64
- **CPU:** AMD Ryzen 9 7900X (12C/24T)
- **Memory:** 64 GB RAM
- **Swap:** zram (4 GB)
- **Primary Disk:** WD_BLACK SN770 1TB (NVMe)
- **Disk / FS:** LUKS encryption + Btrfs

### Disk layout (summary)
- `/boot` (vfat)
- Encrypted root/home volume (LUKS) on NVMe, formatted as Btrfs

