# NAS Inventory (NASA host)

## Storage
- /volume1 (pool1, ext4): primary data + media + docker bind mounts
- /volume2 (pool2, ext4): backup target (restic repo lives here)

## App data roots
- /volume1/docker/joplin
- /volume1/docker/sierrafin
- /volume1/docker/tiktokFin

## Static IP containers (macvlan)
- 192.168.8.50 -> sierrafin (Jellyfin main)
- 192.168.8.211 -> jellyfin_tiktok (Jellyfin short-form)

## Notes
- DNS + reverse proxy are not hosted on the NAS; they live on a separate Debian server.
