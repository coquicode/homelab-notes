# 05. Automatic Ripping Machine (ARM)

**Status:** Running, with one known error left alone on purpose.
**Version:** ARM image 2.24.3 on TrueNAS

## Setup

ARM runs as an image on the TrueNAS server and rips discs into files. Setup details (compose or app settings, drive passthrough): *blank*.

## Renaming "movies" to "Movies"

ARM writes finished rips to a folder named `movies`. I wanted `Movies`. I decided against patching ARM's code and made a symlink instead:

```
ln -s movies Movies
```

Both names now point to the same folder, and ARM's code stays untouched, so updates won't undo the fix.

## MakeMKV error: "application version is too old"

**First seen:** 2026-09-29

MakeMKV is the ripping tool inside ARM. I could have compiled a newer version by hand. I decided not to, and I'm waiting for an official ARM update.

**To do:** Check for an ARM release newer than 2.24.3.

## Related

- [03-truenas-server](03-truenas-server.md)
