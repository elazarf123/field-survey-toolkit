# Site Survey Checklist

Work through each section on site. Mark each item ✅ done, ⚠️ issue found (note it), or N/A. Photograph anything marked ⚠️.

**Site ID:** ____________ **Date:** ____________ **Surveyor:** ____________ **Site contact:** ____________

---

## 1. Site

- [ ] Site ID and room/closet names match what's on the work order
- [ ] Access method recorded (key, badge, escort required, hours of access)
- [ ] Room type noted: MDF / IDF / telecom closet / shared space
- [ ] Room condition: cooling, ventilation, ambient temperature, signs of water or dust
- [ ] Physical security: door locks, cameras, shared with other tenants?
- [ ] Floor plan or sketch showing where the room and racks are
- [ ] Photos: room entrance, room overview from each corner

## 2. Rack

- [ ] Rack ID / label recorded
- [ ] Rack type and size (2-post / 4-post / wall-mount, total U)
- [ ] Rack elevation drawn top to bottom: device, U position, U height
- [ ] Free U space counted
- [ ] Rack grounded and bonded
- [ ] Doors, side panels, and locks present and working
- [ ] Cable management (horizontal/vertical managers) present and usable
- [ ] Photos: rack front, rack rear, close-up of each section

## 3. Device labels and serial plates

For **every** device in or near the rack:

- [ ] Hostname / asset label (physical label on the device)
- [ ] Manufacturer and model
- [ ] Serial number — read from the serial plate and matched against `show inventory` where available
- [ ] Asset tag number (if the organization uses them)
- [ ] Rack U position
- [ ] Label present, legible, and matches documentation? If not, note it
- [ ] Photos: device front, and a clear, glare-free close-up of the serial plate

## 4. Cabling

- [ ] Patch panels identified: panel ID, port count, cable category (Cat5e / Cat6 / Cat6A / fiber)
- [ ] Panel ports labeled and labels match the far-end jacks (spot-check a sample)
- [ ] Switch-to-panel patching recorded (or captured by photo + `show interfaces status`)
- [ ] Uplinks identified: media type (copper / multimode / single-mode fiber), connector (LC / SC), destination
- [ ] Fiber: patch cords and SFP types noted; dust caps on unused ports
- [ ] Cable condition: bend radius, strain relief, no cables across the front of devices
- [ ] Unlabeled or unknown cables flagged
- [ ] Photos: each patch panel, uplink connections, any problem areas

## 5. Power

- [ ] PDUs identified: ID, type (basic / metered / switched), input plug type
- [ ] Circuit / breaker ID feeding each PDU (from panel label if accessible)
- [ ] UPS present? Model, load %, battery age / last test date, runtime estimate
- [ ] Each device's power supplies and which PDU each one is plugged into
- [ ] Redundant power: dual-PSU devices on separate PDUs / circuits?
- [ ] Free outlets on each PDU
- [ ] Power cords labeled or traceable
- [ ] Photos: PDUs, UPS display, breaker panel labels (if accessible)

## 6. Radios and antennas

For wireless access points, point-to-point links, and cellular/backup radios:

- [ ] Device type (indoor AP, outdoor AP, PtP/PtMP radio, cellular gateway)
- [ ] Model, serial, and label (see section 3)
- [ ] Mounting location and height; mount type (ceiling, wall, pole, roof)
- [ ] Antenna type (integrated / external omni / directional / sector) and orientation or azimuth
- [ ] Line of sight to the far end (for PtP links) — note obstructions
- [ ] Power source: PoE from switch port, PoE injector, or local power
- [ ] Coax / Ethernet run to the radio: length, weatherproofing, grounding / lightning protection for outdoor runs
- [ ] Photos: device in place, antenna orientation, mount, cable entry points

## 7. Network capture (read-only)

- [ ] Console or SSH access method confirmed with site contact
- [ ] Captured from each switch — see [`cisco-show-commands.md`](cisco-show-commands.md):
  `show version`, `show inventory`, `show ip interface brief`, `show interfaces status`, `show cdp neighbors`, `show vlan brief`
- [ ] Output saved to a text file named per the photo/file naming standard
- [ ] **No configuration changes made during the survey**

## 8. Close-out

- [ ] All ⚠️ items have a note and a photo
- [ ] Room left as found; doors locked
- [ ] Site contact briefed on anything urgent (safety, power, overheating)
- [ ] Photos and captures copied off the device to approved storage
