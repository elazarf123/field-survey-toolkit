# Field Survey Toolkit

Templates and reference sheets for documenting network and infrastructure sites during field work — the kind of walk-through you do before a refresh, a migration, a new install, or when inheriting a site with no current documentation.

The goal is simple: leave every site with a record that someone who has never been there could use to find the rack, identify the gear, trace the cabling, and understand how the network is laid out.

## What's in here

| File | Use it for |
| :--- | :--- |
| [`site-survey-checklist.md`](site-survey-checklist.md) | Walk-through checklist: site access, racks, device labels and serial plates, cabling, power, radios and antennas |
| [`photo-naming-standard.md`](photo-naming-standard.md) | A consistent file-naming scheme so photos stay sorted and traceable to the checklist |
| [`cisco-show-commands.md`](cisco-show-commands.md) | The core read-only `show` commands to capture from Cisco IOS / IOS-XE switches, and what each one tells you |
| [`sample-survey-report.md`](sample-survey-report.md) | A filled-in example report showing the expected level of detail |

## How to use it

1. **Before the visit:** copy the checklist, fill in what you already know (site ID, contact, scope), and confirm access and escort requirements.
2. **On site:** work the checklist top to bottom. Photograph as you go using the naming standard. Capture the `show` command output from each switch (read-only — no config changes during a survey).
3. **After the visit:** build the report from the template, attach photos and command output, and flag anything that needs follow-up.

## Data handling

Survey records describe real infrastructure, so treat them as sensitive:

- Keep completed surveys, photos, and command output in the client's or employer's approved storage — **not** in a public repo.
- Everything in this repository is a template or uses **fictional, sanitized data**. No real organizations, IP addresses, serial numbers, or site locations appear here.
- Before sharing any output, redact IP addresses, hostnames that reveal location or ownership, serial numbers, and SNMP/credential strings.

## License

MIT — use and adapt freely.
