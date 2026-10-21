# 02. Network Upgrade Plan (UniFi 10GbE)

**Status:** Planned. Nothing has been bought or installed.

## Goals

- More granular control than the current router provides.
- Faster Ethernet.
- 10GbE ports, so I don't have to upgrade again soon.
- Everything mounted in a rack.

## Options considered

- Several options that keep the current router in bridge (modem-only) mode, with new gear doing the routing behind it.
- One option that adds a new standalone modem.

**Decision:** Not made yet.

## Reference build

| Part | Role |
| --- | --- |
| UniFi Cloud Gateway Fiber (UCG-Fiber) | Router/gateway |
| UniFi Pro XG 8 PoE | 10GbE switch with PoE |
| UniFi U7 Pro | Wi-Fi access point |

Check current specs and port counts on the manufacturer's site before buying. Models and prices change.

## Future equipment suggestions

These are categories to think about when I get to the cables and mounting part of the parts list. None are chosen.

| Category | Why it matters | Things to check |
| --- | --- | --- |
| Rack | Holds everything and keeps it tidy | Depth for the NAS and any shelf-mounted gear; wall-mount or open-frame; number of rack units needed with room to grow |
| Patch panel and keystone jacks | Clean, labeled runs to wall ports | Number of runs; shielded or unshielded |
| Copper cabling | Connects 10GbE devices over RJ45 | Cable category rated for 10GbE at the length of each run |
| SFP+ DAC or fiber | Short, low-power links between switch and gateway | Port types on both ends; cable length; vendor compatibility |
| Rack shelf | Mounts devices that aren't rack-mountable | Weight rating; depth |
| UPS | Keeps the NAS and network up through brief outages and allows clean shutdown | Capacity in VA/watts; runtime; whether the NAS can be shut down automatically on battery |
| Power strip or PDU | Power distribution in the rack | Outlet count; surge protection |
| Cable management | Strain relief, labels, velcro ties | Label scheme decided up front |
| Extra access points | Better Wi-Fi coverage | House layout; PoE budget on the switch |

## Questions to settle before buying

1. Which option for the CAX30: bridge mode or a new modem?
2. What connection type does my ISP provide, and what does that need at the gateway?
3. How many devices truly need 10GbE, and what are the NAS's NIC speeds?
4. How much PoE power will the access points and any cameras draw?
5. How will I separate the security lab from the rest of the network? See [07-security-lab](07-security-lab.md).

## Related

- [01-home-network](01-home-network.md)
