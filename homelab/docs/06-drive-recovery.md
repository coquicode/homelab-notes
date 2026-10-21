# 06. Failing-Drive Data Recovery

**Status:** Documented. Part of the recovery used the NAS.

## Problem

A 1.5 TB Seagate external drive (volume `<drive-label>`) used to have three partitions: EFI, HFS+ and a FAT32-labeled one. The FAT32 partition's GPT entry disappeared, leaving only EFI and HFS+. The missing partition was no bigger than 500 GB and may have been reformatted at some point under the same name.

The drive's original SATA/USB adapter had stopped working, so I used a different one.

## Approach

Never scan the original drive more than necessary. Image it first, then work on the image.

1. Booted an Intel iMac from a SystemRescue live USB to work from Linux.
2. Confirmed the drive's real capacity was 1.5 TB.
3. Read SMART data:

| Attribute | Value |
| --- | --- |
| Reallocated_Sector_Ct | 1312 |
| Current_Pending_Sector | 0 |
| UDMA_CRC_Error_Count | 0 |

4. Cloned the whole drive with `ddrescue` to an image on a 2 TB SanDisk Extreme SSD, formatted ext4 for the job. Result: 100% rescued, 0 errors.
5. Ran a TestDisk deep scan and a PhotoRec free-space scan against the image.
6. Mounted a TrueNAS SMB share (`shared`) and pointed PhotoRec's output at a `photorec` subfolder on it.

## Results

PhotoRec mostly found files that were already on the readable HFS+ partition, plus some `.gz` files that wouldn't expand and `.mov` files that wouldn't play.

| .mov result | Count |
| --- | --- |
| Total recovered | 2,453 |
| Play fine | 2,043 |
| Missing moov atom | 403 |
| Other errors | 7 |

## Lessons

- Image first, scan the image. It protects a drive that may be failing.
- A rescued image with 0 errors means the drive's readable data was captured in full.
- Carving tools like PhotoRec recover files without names or folders and often return damaged video.

## Related

- [03-truenas-server](03-truenas-server.md)
- [Glossary](../GLOSSARY.md)
