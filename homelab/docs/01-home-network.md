# 01. Home Network

**Status:** Active
**Router:** Netgear Nighthawk CAX30

## Overview

The CAX30 is the current router. Two things have come up with it: devices showing as blocked, and setting up link aggregation so the NAS can use both of its network ports. A replacement is planned in [02-network-upgrade-plan](02-network-upgrade-plan.md).

## Devices blocked that I never blocked

**Symptom:** Several devices appeared as blocked on the router, and I hadn't blocked any of them.

**Timing:** A firmware update happened around the same time the problem began, so the update is the prime suspect.

**Resolution:** Not recorded.

### What to check if it happens again

- Whether the entries are in the device list or in access-control or parental-control settings.
- Whether the update reset any of those settings to defaults.
- The firmware version before and after the update.

## Link aggregation for the NAS

**Goal:** Let both NIC ports on the NAS carry traffic.

**Approach:** Configure link aggregation on router LAN ports 1 and 2. The NAS side must be set to the same mode, or the link won't behave correctly.

| Detail | Value |
| --- | --- |
| Router ports used | 1 and 2 |
| Aggregation mode (router) | |
| Aggregation mode (NAS) | |
| Completed? | |

**Limitation to remember:** Aggregation spreads multiple connections across the links. A single transfer from one device usually still runs at the speed of one link.

## Related

- [03-truenas-server](03-truenas-server.md)
- [Glossary: link aggregation](../GLOSSARY.md)
