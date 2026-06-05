# Hardware & Node Ledger

Physical inventory for the Proxmox home lab — compute, networking, and storage.

---

## Compute Nodes

### pve-whitewalker — Primary Hypervisor

| Field    | Details                                                        |
|----------|----------------------------------------------------------------|
| Hardware | Dell OptiPlex 7070                                             |
| CPU      | Intel i5-9500 @ 3.00 GHz (6c/6t)                              |
| RAM      | 16 GB                                                          |
| Storage  | 256 GB SSD (boot/VMs) + 1 TB HDD (LXC) + LaCie 8 TB (media)  |
| Network  | Ethernet — EdgeRouter X                                        |
| Role     | Primary hypervisor, media host, security lab                   |
| Status   | Online                                                         |

**Hosted services:** Jellyfin/media stack, WireGuard, CSI Linux OSINT VM,
Cloudflare Tunnel

---

## Networking

### Ubiquiti UniFi Dream Router 7 (UDR7)

| Field    | Details                                                        |
|----------|----------------------------------------------------------------|
| Role     | Primary home router / WAN gateway                              |
| Features | WireGuard VPN server (subnet `192.168.4.0/24`), port forwarding to EdgeRouter X |
| Notes    | Static route configured to lab subnet via EdgeRouter X         |

**WireGuard clients:** Work laptop, phone, personal laptop

---

### Ubiquiti EdgeRouter X

| Field    | Details                                                        |
|----------|----------------------------------------------------------------|
| Role     | Lab gateway / inter-VLAN router                                |
| Features | VLAN trunking, inter-VLAN routing, NAT masquerade, firewall    |
| Notes    | All lab VLANs trunked on uplink NIC to Proxmox host. Sandbox traffic hard-blocked at this layer. |

See [VLAN Registry](../networking/vlan-registry.md) for full segmentation details.

---

## Storage

| Device         | Capacity | Attached To     | Use                     |
|----------------|----------|-----------------|-------------------------|
| SSD (internal) | 256 GB   | pve-whitewalker | Proxmox boot, VM disks  |
| HDD (internal) | 1 TB     | pve-whitewalker | LXC storage             |
| LaCie USB HDD  | 8 TB     | pve-whitewalker | Media library (Jellyfin)|

---

## Network Topology
