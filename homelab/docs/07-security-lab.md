# 07. Self-Hosted Security Lab

**Status:** Planned. Nothing is installed yet.

## Goal

Learn cybersecurity on my own equipment with an environment similar to TryHackMe: practice attacking and defending, solve challenges and build skills in offensive and defensive security.

## Hardware situation

- Daily-use computers
- One extra machine: the Ugreen DXP6800 Pro
- No separate server with the 16 to 32 GB of RAM originally suggested for a lab
- The NAS's current configuration and role still need to be pinned down

| Detail needed | Value |
| --- | --- |
| CPU | |
| RAM | |
| Storage | |
| Current OS and workload | |

## Main concern: isolation

Deliberately vulnerable machines must not be able to reach anything important. A compromised lab VM could attack other devices if the network allows it. The lab must not reach:

- Backup servers and backup storage
- Personal computers and files
- Other important home-network devices

## Planned design

- **Normal network:** daily-use systems and important files.
- **Lab network:** the lab host and its virtual machines.
- **Firewall rules:** block lab traffic to the normal LAN and to backups.
- **Snapshots:** roll lab machines back after experiments go wrong.

A separate physical server adds another layer of separation, but isn't required. Isolation is essential either way. The [UniFi upgrade](02-network-upgrade-plan.md) would make VLANs and firewall rules easier.

## Platform options

| Option | Best for |
| --- | --- |
| Proxmox VE | Running several isolated virtual machines |
| Linux + Docker | Lightweight web-security labs and vulnerable apps |
| One or two lightweight VMs | Starting small on limited resources |

## Candidate training targets

- Kali Linux: security testing workstation
- OWASP Juice Shop: web application security
- DVWA: deliberately vulnerable web app
- Metasploitable: vulnerable Linux target
- Windows and Active Directory environments: later, as the lab grows

## Next steps

1. Record the NAS hardware in the table above.
2. Decide between Proxmox and Docker based on available RAM.
3. Design the lab network and firewall rules before installing any vulnerable machine.
4. Start with TryHackMe, then move to the local lab.

## Related

- [03-truenas-server](03-truenas-server.md)
- [Glossary](../GLOSSARY.md)
