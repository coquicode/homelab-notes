# 04. Photo Migration and Immich

**Status:** Completed. Immich is working.

## Goal

Move a photo collection of about 1.12 TB onto the NAS, then keep an independent, browsable copy in Immich so I can reorganize the original folder freely.

## Part 1: Transfer with rsync

| | Path |
| --- | --- |
| Source | `/mnt/tank/private/<source-dir>/` |
| Destination | `/mnt/tank/shared/<destination-dir>/` |

### SSH problem

I tried to connect over SSH with the admin account and a downloaded key file. It failed with an "invalid format / access denied" error. Troubleshooting took a long time, so I switched to running `rsync` locally on the server.

### Timeouts

An interactive `rsync` session kept timing out. Running it in the background with `nohup` was suggested, because the job keeps going if the session drops.

Example pattern (adjust paths):

```
nohup rsync -avh --progress "<source>/" "<destination>/" > rsync.log 2>&1 &
```

### Verification

A dry run reported:

```
sent 1.43M bytes  received 6.04K bytes  10.24K bytes/sec
total size is 1.12T  speedup is 777,912.86 (DRY RUN)
```

No files were listed for transfer, which is strong evidence the destination matches the source. Disk usage was about 1007 GB at the source and 1006 GB at the destination. A small gap like that is not proof of missing data, because filesystems report allocation differently.

**Limit of this check:** A normal dry run compares file size and modification time, not contents. A checksum comparison (`rsync -c` with `--dry-run`) is slower but verifies contents.

**Rule:** Keep the source until the destination is independently verified and backed up.

## Part 2: Grayed-out folder on macOS

A folder showed as grayed out in Finder. Steps taken:

1. Cleared extended attributes with `xattr -c`.
2. Confirmed `SetFile` exists at `/usr/bin/SetFile`.
3. Was instructed to change the folder's creation date with `SetFile -d`.

**Outcome:** Not recorded.

## Part 3: Immich

### Managed library vs external library

I wanted Immich to hold its own copy of the photos so changes to the original folder wouldn't affect it. That points to the managed library.

| Feature | Managed library | External library |
| --- | --- | --- |
| Stores an independent copy | Yes | No |
| Changes to the original affect Immich | No, after a successful upload | They can |
| Immich manages its own storage | Yes | No, I manage the source files |
| Fits my goal | Yes | No |

### Workflow

1. Keep the transferred collection intact on the server.
2. Upload it into Immich's managed storage.
3. Verify photos and videos uploaded and open correctly.
4. Keep an additional independent backup.
5. After verifying, modify the original freely.

**Caveat:** If the original and the managed library sit on the same pool, a pool failure can destroy both. Immich's copy isn't a disaster-proof backup by itself.

### File formats

HEIC and MOV files are supported. iPhone Live Photos can be paired with their video. I kept the original formats instead of converting. Immich may transcode video for playback but keeps the original upload.

### Failed uploads

Some uploads failed. The web uploader doesn't appear to offer a "Retry all" control. Re-uploading the originals is a workable fallback, because Immich's deduplication recognizes assets it already has.

**How it was finally resolved:** Not recorded.

## Related

- [03-truenas-server](03-truenas-server.md)
- [Glossary](../GLOSSARY.md)
