# 🖥️ Homelab

Proxmox-based home lab built for security research, OSINT investigations,
and malware analysis. Segmented into isolated VLANs with dedicated 
environments for each use case.

## Lab Overview

| Component     | Details                          |
|---------------|----------------------------------|
| Hypervisor    | Proxmox VE                       |
| Primary Node  | pve-whitewalker                  |
| Lab Subnet    | 172.16.10.0/24                   |
| Network       | EdgeRouter X (VLAN trunking)     |

## VLAN Segments

| VLAN | Name            | Purpose                          | Internet        |
|------|-----------------|----------------------------------|-----------------|
| 10   | Management      | Proxmox UI, SSH, admin           | Restricted      |
| 20   | Media / Home    | Plex, general devices            | Yes             |
| 30   | Research Lab    | OSINT / CSI Linux                | ProtonVPN only  |
| 66   | Malware Sandbox | Malware analysis, threat research| None (air-gap)  |

## Active VMs / Services

- **CSI Linux (VM 105)** — OSINT research, Maltego, SpiderFoot. All traffic via ProtonVPN WireGuard.
- **Malware Sandbox (VLAN 66)** — Air-gapped. Flare-VM / REMnux for detonation and analysis.
- **Jellyfin (LXC 102)** — Media stack on VLAN 20.

## Documentation
- [Hardware & Node Ledger](hardware/node-ledger.md)
- [VLAN Registry](networking/vlan-registry.md)
- [CSI Linux OSINT VM](vms/csi-linux-osint.md)
- [Service Map](services/service-map.md)
