# Photo Naming Standard

Consistent names make photos sortable, searchable, and traceable to the checklist without opening each one.

## Format

```
<SITE>_<ROOM>_<RACK>_<CATEGORY>_<SUBJECT>_<SEQ>.jpg
```

| Field | Rule | Examples |
| :--- | :--- | :--- |
| `SITE` | Site ID from the work order. Uppercase, no spaces. | `SITE01`, `EXS-0042` |
| `ROOM` | Room/closet ID. | `MDF`, `IDF2`, `RM114` |
| `RACK` | Rack ID, or `NA` if not rack-related. | `R01`, `R02`, `NA` |
| `CATEGORY` | One of the codes below. | `DEV` |
| `SUBJECT` | Short description; device label, U position, or panel ID. Hyphens, not spaces. | `SW01-front`, `U24-serial`, `PP-A` |
| `SEQ` | Two-digit sequence number for multiple shots of the same subject. | `01`, `02` |

## Category codes

These map to the sections of the site survey checklist.

| Code | Meaning |
| :--- | :--- |
| `SITE` | Room overview, entrance, floor plan, environment |
| `RACK` | Rack front/rear, elevation, cable management |
| `DEV` | Device front/rear |
| `SER` | Serial plate / asset tag close-up |
| `CAB` | Patch panels, uplinks, fiber, cable runs |
| `PWR` | PDUs, UPS, breaker labels, power cords |
| `RF` | Radios, APs, antennas, mounts |
| `ISSUE` | Anything flagged ⚠️ on the checklist |

## Examples

```
SITE01_MDF_NA_SITE_room-overview_01.jpg
SITE01_MDF_R01_RACK_front_01.jpg
SITE01_MDF_R01_RACK_rear_01.jpg
SITE01_MDF_R01_DEV_SW01-front_01.jpg
SITE01_MDF_R01_SER_SW01-serial_01.jpg
SITE01_MDF_R01_CAB_PP-A_01.jpg
SITE01_MDF_R01_PWR_PDU-A_01.jpg
SITE01_IDF2_NA_RF_AP-2F-east_01.jpg
SITE01_MDF_R01_ISSUE_unlabeled-uplink_01.jpg
```

## Rules

- **No spaces** anywhere in the name. Use `_` between fields and `-` inside a field.
- **Uppercase** for IDs and category codes; lowercase is fine for the subject.
- **One subject per photo.** If a serial plate is in a wide shot, take a separate `SER` close-up.
- **Rename the same day**, before details are forgotten. Keep the camera's original filename in a notes column if needed.
- Command captures follow the same pattern with a `CLI` category and `.txt` extension:
  `SITE01_MDF_R01_CLI_SW01-show-inventory_01.txt`

## Before you share

Serial plates, labels, and screens often show sensitive details. Before photos leave approved storage, blur or crop serial numbers, IP addresses, hostnames that reveal ownership or location, and anything written on whiteboards or stickers.
