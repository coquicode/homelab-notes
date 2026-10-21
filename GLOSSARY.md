# Glossary

Short definitions for terms used across these notes.

**10GbE:** Ethernet running at 10 gigabits per second.

**ARM (Automatic Ripping Machine):** Software that automatically rips discs when they're inserted.

**Bridge mode:** A router setting that turns it into a simple modem so another device does the routing.

**CORE (TrueNAS CORE):** The FreeBSD-based edition of TrueNAS. Compare SCALE.

**Cron job:** A command scheduled to run at set times. In TrueNAS: System Settings > Advanced.

**DAC (direct attach copper):** A pre-terminated cable for short SFP+ links between devices.

**Dataset:** A filesystem inside a ZFS pool with its own permissions, snapshots, compression, quotas, encryption and sharing settings.

**Deduplication:** Recognizing files already stored so they aren't saved twice. Immich uses it to skip assets it already has.

**ddrescue:** A Linux tool that copies a failing drive, retrying and skipping bad areas, and logs what it recovered.

**GPT:** The partition table format that records a disk's partitions.

**HEIC:** The image format iPhones use by default.

**HFS+:** An older Apple filesystem.

**Immich:** A self-hosted photo and video library.

**IronWolf Pro:** Seagate's NAS-rated hard drive line.

**Link aggregation:** Combining multiple network ports into one logical link for more total throughput and redundancy. Both ends must use the same mode. A single transfer usually still uses one link.

**MakeMKV:** The disc-ripping tool used inside ARM.

**Managed library (Immich):** Immich stores its own copy of uploaded files. Compare external library, where Immich reads files you manage yourself.

**midclt:** The TrueNAS command-line client for its middleware.

**moov atom:** The part of a `.mov` or `.mp4` file holding playback information. Without it, a video usually won't play.

**NAS (network-attached storage):** A storage device on the network that serves files to other devices.

**NIC:** Network interface card, the network port.

**nohup:** Runs a command that keeps going after the terminal session closes.

**PhotoRec:** A tool that carves files out of raw disk data without relying on the filesystem.

**PoE (Power over Ethernet):** Delivering power to a device over the network cable.

**Pool:** In ZFS, the storage capacity built from one or more groups of drives.

**Proxmox VE:** A virtualization platform for running VMs and containers.

**rsync:** A tool that copies and synchronizes files, transferring only differences. `--dry-run` shows what would change without changing anything.

**SCALE (TrueNAS SCALE):** The Linux-based edition of TrueNAS.

**SetFile:** A macOS command-line tool for file attributes such as the creation date.

**SFP+:** A pluggable port type for 10-gigabit copper or fiber modules and cables.

**SMART:** A drive's built-in health reporting.

**SMB:** The file-sharing protocol used by Windows and macOS.

**Snapshot:** A point-in-time copy of a dataset that makes it possible to recover earlier versions of files.

**SSH:** Secure remote terminal access.

**Symlink:** A shortcut that points one path at another (`ln -s target link`).

**SystemRescue:** A Linux live USB with recovery tools.

**TestDisk:** A tool that finds lost partitions and repairs partition tables.

**VLAN:** A logical network separation on the same physical hardware.

**xattr:** macOS extended file attributes. `xattr -c` clears them.

**zvol:** A virtual block device inside a ZFS pool, used for VM disks or iSCSI.
