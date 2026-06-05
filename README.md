# 🖥️ Homelab

Proxmox-based home lab built for security research, OSINT investigations,
and malware analysis. Segmented into isolated VLANs with dedicated
environments for each use case.

## Lab Overview

| Component  | Details                      |
|------------|------------------------------|
| Hypervisor | Proxmox VE                   |
| Primary Node | pve-whitewalker            |
| Network    | EdgeRouter X (VLAN trunking) |
| Gateway    | Ubiquiti UniFi Dream Router 7|

## VLAN Segments

| VLAN | Name            | Purpose                           | Internet         |
|------|-----------------|-----------------------------------|------------------|
| 10   | Management      | Proxmox UI, SSH, admin            | Restricted       |
| 20   | Media / Home    | Plex, general devices             | Yes              |
| 30   | Research Lab    | OSINT / CSI Linux                 | ProtonVPN only   |
| 66   | Malware Sandbox | Malware analysis, threat research | None (air-gapped)|

## Active VMs / Services

- **CSI Linux** — OSINT research, Maltego, SpiderFoot. All egress via ProtonVPN WireGuard.
- **Malware Sandbox** — Air-gapped VLAN 66. Flare-VM / REMnux for detonation and analysis.
- **Plex** — Media stack, isolated on VLAN 20.

## Documentation

- [Hardware](hardware.md)
- [VLAN Registry](networking/vlan-registry.md)
- [CSI Linux OSINT VM](vms/csi-linux-osint.md)
- [InstallFix Infostealer — IR Walkthrough](incidents/installfix-infostealer.md)
