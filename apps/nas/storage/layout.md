# Storage Layout

## Volume 1 (primary)
- App configs and bind mounts:
  - /volume1/docker/<stack>/{config,cache,data,...}
- Media:
  - /volume1/Media/Movies
  - /volume1/Media/Episodes
  - /volume1/Media/Music
- Short-form media:
  - /volume1/Sunder

## Volume 2 (backup)
- Restic repository location:
  - /volume2/restic-repo

## Docker engine internals
- The NAS platform stores docker overlay data under:
  - /volume1/@docker/overlay2/...
Do not touch these directly; use Docker tooling.
