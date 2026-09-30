# Cisco Show Commands for Site Surveys

Read-only commands to capture from Cisco IOS / IOS-XE switches during a survey. None of these change configuration.

Before capturing, run `terminal length 0` so output isn't paused at `--More--`, and log your session to a text file named per the [photo naming standard](photo-naming-standard.md) (category `CLI`).

---

## `show version`

**What it tells you:**

- Software version and image — needed to check support status and known bugs
- Model number and system serial number
- Uptime — a very long uptime can mean no patching; a very short one can mean recent crashes or power loss
- Last reload reason (power loss, crash, manual reload)
- Memory and license level

**Survey use:** confirms what the device is and what it's running, and flags stability or patching concerns.

## `show inventory`

**What it tells you:**

- Every hardware component the switch detects: chassis, stack members, power supplies, fan trays, line cards, and installed SFP/transceiver modules
- Product ID (PID) and serial number (SN) for each

**Survey use:** the authoritative serial list. Cross-check each chassis serial against the physical serial plate you photographed, and record SFP types for the cabling section.

## `show ip interface brief`

**What it tells you:**

- Each interface (physical and VLAN/SVI) with its IP address, if any
- Status (administrative) and Protocol (line) — up/up, down/down, or administratively down

**Survey use:** fast summary of which interfaces have Layer 3 addresses — typically the management VLAN interface — and which are up. `up/down` usually means a physical or cabling problem on that port.

## `show interfaces status`

**What it tells you:**

- Every switch port with its description, status (connected / notconnect / disabled / err-disabled), VLAN (or `trunk`), duplex, speed, and media type

**Survey use:** the best single view of port utilization. Count free ports, spot `err-disabled` ports, find half-duplex or low-speed links that suggest bad cabling, and compare port descriptions with what's physically patched.

## `show cdp neighbors`

**What it tells you:**

- Directly connected Cisco (and some other CDP-capable) devices: neighbor device ID, local port, remote port, platform, and capability (switch, router, phone, AP)

**Survey use:** maps the physical topology without tracing cables — which switch uplinks to which, and where APs and phones are connected. Use `show cdp neighbors detail` to also see neighbor management IPs and software versions. If CDP is disabled, try `show lldp neighbors`.

## `show vlan brief`

**What it tells you:**

- Each VLAN ID and name, its status, and which access ports are assigned to it (trunk ports are not listed here)

**Survey use:** documents the VLAN layout — user, voice, wireless, management, and so on — and shows unused VLANs or ports sitting in the default VLAN 1 that may need cleanup.

---

## Quick capture block

```
terminal length 0
show version
show inventory
show ip interface brief
show interfaces status
show cdp neighbors
show vlan brief
```

## Sanitizing output before sharing

Command output contains details that identify a real network. Before it goes anywhere outside approved storage, redact:

- IP addresses and subnets
- Serial numbers
- Hostnames and port descriptions that reveal the organization or location
- Neighbor device IDs from `show cdp neighbors`
