# 03. TrueNAS Server

**Status:** Active
**Hardware:** Ugreen DXP6800 Pro (6-bay)
**OS:** TrueNAS SCALE 25.10.7 (Goldeye branch)

## Purpose

- Media center for movies and music
- Photo backup from my devices (see [04-photo-migration-and-immich](04-photo-migration-and-immich.md))
- General document backup
- Possible homelab use later (see [07-security-lab](07-security-lab.md))
- No transcoding above 1080p planned, which keeps the hardware requirements modest

## Hardware

| Item | Detail |
| --- | --- |
| Chassis | Ugreen DXP6800 Pro, 6 bays |
| Drives | Seagate IronWolf Pro, 12 TB each |
| Drive count | |
| CPU | |
| RAM | |
| Boot device | |
| NIC ports and speeds | |

## Build process

### 1. Decide what the server is for

I settled on the use cases above before buying, and chose NAS-rated drives for always-on use.

### 2. Work out which TrueNAS I'm running

I assumed I was on TrueNAS CORE. The console menu showed "Open TrueNAS CLI Shell" and "Open Linux Shell," which is SCALE wording. SCALE is Linux-based, and CORE is FreeBSD. Advice written for one can be wrong for the other, so check the edition before following a guide.

### 3. Create the pool

| Detail | Value |
| --- | --- |
| Pool name | `tank` |
| Layout (RAID level) | |
| Number of vdevs | |
| Compression | |

### 4. Plan datasets before moving data

A dataset is a filesystem inside a pool. It's like a folder, but with its own permissions, snapshots, compression, quotas, encryption and sharing settings. Separate datasets let me configure data groups independently. Plan the layout before copying large amounts of data onto the server.

| Term | Meaning | Example |
| --- | --- | --- |
| Pool | The capacity provided by the drives | `tank` |
| Dataset | A filesystem inside the pool | `tank/media` |
| Folder | A directory inside a dataset | `tank/media/movies` |
| Snapshot | A point-in-time version of a dataset | |
| zvol | A virtual block device for VM disks or iSCSI | |

Example structure:

```
tank                  # pool
|-- media             # dataset
|   |-- movies        # folder
|   '-- tv            # folder
|-- documents         # dataset
|-- backups           # dataset
'-- virtual-machines  # dataset or parent for VM storage
```

Rules of thumb:

1. Make a separate dataset when data needs different permissions, snapshots, encryption, quotas, replication or sharing.
2. Use ordinary folders when data can share one configuration.
3. Don't create a dataset for every folder without a reason.
4. Use datasets for file storage and zvols for block storage such as virtual disks.

My pool has datasets named `shared` and `private`. Full list of datasets: *blank*.

### 5. Copy data in

I copied data from a portable drive first. The rule I followed was to verify the copy on the NAS before deleting anything from the source. The larger photo transfer is documented in [04](04-photo-migration-and-immich.md).

### 6. Use both network ports

I configured link aggregation on the router. See [01-home-network](01-home-network.md).

### 7. Add services

- SMB shares for file access
- Immich for photos
- ARM for ripping discs ([05-arm-ripper](05-arm-ripper.md))

## One-time scheduled shutdown

**Goal:** Shut the server down once at a specific date and time, not on a recurring schedule.

**Where:** System Settings > Advanced > Cron Jobs.

**What I established:**

1. Cron jobs can run commands at a schedule.
2. A cron job can be set for a specific date and time. Disable or delete it afterward so it doesn't run again in a future year.
3. The TrueNAS middleware shutdown is preferable to bypassing TrueNAS's normal shutdown handling.

**Candidate commands** (run as `root`):

```
# Unverified on my install
/usr/bin/midclt call system.shutdown "Scheduled shutdown"

# Verified path on my install
/usr/sbin/shutdown --poweroff
```

**Warning:** Don't run either command until you intend to shut down the server.

**Status:** Date and time not chosen yet.

## Open items

- Fill in the blank hardware and pool details above.
- Choose the shutdown date and confirm the middleware command works.

## Related

- [01-home-network](01-home-network.md)
- [Glossary](../GLOSSARY.md)
