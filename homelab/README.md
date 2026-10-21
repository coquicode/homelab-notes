# Homelab Notes

A personal reference for my home network and TrueNAS server: how it was built, what broke, how I fixed it, and what I plan to do next. I'm publishing it in case the process helps someone else, and so future-me can remember why I made each decision.

Everything identifying (usernames, key names, IP addresses, folder names, volume labels) has been replaced with placeholders such as `<NAS_IP>` or `<source-dir>`.

## Status at a glance

| Project | Status | Doc |
| --- | --- | --- |
| Home router (Netgear Nighthawk CAX30) | Active | [01-home-network](docs/01-home-network.md) |
| 10GbE network upgrade (UniFi) | Planned, not started | [02-network-upgrade-plan](docs/02-network-upgrade-plan.md) |
| TrueNAS server (Ugreen DXP6800 Pro) | Active | [03-truenas-server](docs/03-truenas-server.md) |
| Photo migration and Immich | Completed | [04-photo-migration-and-immich](docs/04-photo-migration-and-immich.md) |
| Automatic Ripping Machine (ARM) | Running, one known error | [05-arm-ripper](docs/05-arm-ripper.md) |
| Failing-drive data recovery | Documented | [06-drive-recovery](docs/06-drive-recovery.md) |
| Self-hosted security lab | Planned, not started | [07-security-lab](docs/07-security-lab.md) |

New to a term? See the [glossary](GLOSSARY.md).

## How the pieces connect

```
Internet
   |
Netgear Nighthawk CAX30 (router)
   |   LAN ports 1 and 2 (link aggregation)
Ugreen DXP6800 Pro running TrueNAS SCALE
   |-- ZFS pool "tank": datasets "shared" and "private"
   |-- SMB shares
   |-- Immich (photo library)
   '-- ARM (disc ripping)
```

## Conventions

- `<PLACEHOLDER>` marks a value I redacted.
- **Blank** means I haven't recorded the detail yet. I left it empty rather than guess.
- **Unverified** marks a command or setting I haven't confirmed works on my system. Read it before you run it.
- Commands are examples. Check them against your own paths and versions.

## Disclaimer

These are notes from my own setup, not a tutorial. Commands that delete, format or shut things down can cause data loss. Back up first.
