# Site Survey Report — SAMPLE

> **This is a fictional example.** The site, organization, device labels, serial numbers, and addresses below are invented placeholders for illustration only. IP addresses are shown as `x.x.x.x` and serials use an obviously fake `SN-EXAMPLE-####` format.

| Field | Value |
| :--- | :--- |
| Site ID | EXAMPLE-SITE-01 |
| Organization | Example Organization (fictional) |
| Location | Example Building, 2nd floor (fictional) |
| Survey date | 2026-01-15 |
| Surveyor | J. Doe |
| Scope | Pre-refresh survey of MDF and one IDF; access switching and wireless |

---

## 1. Summary

The MDF and IDF2 were surveyed. The site has two access switches, one core/distribution switch, four wireless APs, and one UPS. Overall condition is fair. **Three follow-up items** were found: one switch on a single power supply, unlabeled uplink fiber in IDF2, and an access switch running software well past its last update.

## 2. Site

| Room | Type | Access | Cooling | Notes |
| :--- | :--- | :--- | :--- | :--- |
| MDF | Dedicated closet | Badge, escort not required | Dedicated split unit, ~70 °F | Clean, locked |
| IDF2 | Shared janitorial room | Key from facilities | None; ~84 °F measured | ⚠️ Warm; shared with cleaning supplies |

## 3. Rack elevation — MDF, Rack R01 (42U, 4-post)

| U | Device | Label | Model | Serial |
| :--- | :--- | :--- | :--- | :--- |
| 42 | Patch panel A (48-port Cat6) | PP-A | — | — |
| 41 | Horizontal cable manager | — | — | — |
| 40 | Core switch | CORE-SW01 | Catalyst 9300-48P | SN-EXAMPLE-0001 |
| 38 | Access switch | ACC-SW01 | Catalyst 9200-48P | SN-EXAMPLE-0002 |
| 36 | Fiber patch panel (12-port LC) | FP-A | — | — |
| 2–3 | UPS | UPS-01 | 1500 VA rackmount | SN-EXAMPLE-0003 |
| 1 | PDU (switched, rear) | PDU-A | — | — |

Free space: 30U.

## 4. Device labels and serial plates

| Label | Physical label present | Plate serial matches `show inventory` | Photo |
| :--- | :--- | :--- | :--- |
| CORE-SW01 | Yes | Yes | `EXAMPLE-SITE-01_MDF_R01_SER_CORE-SW01-serial_01.jpg` |
| ACC-SW01 | Yes | Yes | `EXAMPLE-SITE-01_MDF_R01_SER_ACC-SW01-serial_01.jpg` |
| ACC-SW02 (IDF2) | ⚠️ No — handwritten tape only | Yes | `EXAMPLE-SITE-01_IDF2_R01_SER_ACC-SW02-serial_01.jpg` |

## 5. Cabling

- PP-A: 48 ports Cat6, 31 patched, labels match far-end jacks on a 10-jack spot check.
- Uplink CORE-SW01 → ACC-SW02: single-mode fiber, LC, via FP-A port 1–2.
- ⚠️ IDF2: fiber patch cord to ACC-SW02 uplink is unlabeled at both ends.
- Cable management acceptable in MDF; IDF2 patch cords draped across the front of the switch.

## 6. Power

| PDU | Fed from | Devices | Free outlets |
| :--- | :--- | :--- | :--- |
| PDU-A | UPS-01 | CORE-SW01 (PSU1), ACC-SW01 | 4 |
| Wall outlet | Circuit label unreadable | CORE-SW01 (PSU2) | — |

- UPS-01 load 38%, estimated runtime 22 min, battery date label 2023.
- ⚠️ ACC-SW02 (IDF2) has a single power supply on a non-UPS wall outlet.

## 7. Radios and antennas

| Label | Type | Location | Mount | Power | Antenna |
| :--- | :--- | :--- | :--- | :--- | :--- |
| AP-2F-E | Indoor AP | 2F east hallway | Ceiling | PoE, ACC-SW01 Gi1/0/12 | Integrated |
| AP-2F-W | Indoor AP | 2F west hallway | Ceiling | PoE, ACC-SW01 Gi1/0/13 | Integrated |
| AP-2F-CONF | Indoor AP | 2F conference room | Ceiling | PoE, ACC-SW02 Gi1/0/5 | Integrated |
| AP-LOBBY | Indoor AP | Lobby | Wall | PoE, ACC-SW02 Gi1/0/6 | Integrated |

No outdoor radios or point-to-point links at this site.

## 8. Network capture summary

Full output saved as `EXAMPLE-SITE-01_MDF_R01_CLI_<device>-<command>_01.txt`.

| Device | Software | Uptime | Mgmt IP | Ports used / total | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| CORE-SW01 | IOS-XE 17.x | 94 days | x.x.x.x | 18 / 48 | — |
| ACC-SW01 | IOS-XE 17.x | 94 days | x.x.x.x | 29 / 48 | 1 port err-disabled (Gi1/0/40) |
| ACC-SW02 | IOS-XE 16.x | 3 years+ | x.x.x.x | 11 / 48 | ⚠️ Old release, no reloads = no patching |

**VLANs (from `show vlan brief`):**

| VLAN | Name | Purpose |
| :--- | :--- | :--- |
| 10 | USERS | Wired users |
| 20 | VOICE | IP phones |
| 30 | WIFI | Wireless clients |
| 99 | MGMT | Switch/AP management |
| 1 | default | ⚠️ 6 unused ports still assigned |

**Topology (from `show cdp neighbors`):** CORE-SW01 ↔ ACC-SW01 (copper), CORE-SW01 ↔ ACC-SW02 (fiber), APs on access switches as listed above.

## 9. Follow-up items

| # | Item | Priority | Recommendation |
| :--- | :--- | :--- | :--- |
| 1 | ACC-SW02 on single PSU, no UPS | High | Add UPS or move to protected circuit |
| 2 | ACC-SW02 software 3+ years old | High | Schedule upgrade during refresh window |
| 3 | IDF2 temperature ~84 °F, no cooling | Medium | Add ventilation or relocate gear |
| 4 | Unlabeled IDF2 uplink fiber | Medium | Label both ends |
| 5 | ACC-SW02 missing printed label | Low | Apply standard printed label |
| 6 | Unused ports in VLAN 1 | Low | Move to a parking VLAN and shut down |

## 10. Attachments

- Photos (43), named per the photo naming standard
- CLI captures (18 files, 6 commands × 3 switches)
