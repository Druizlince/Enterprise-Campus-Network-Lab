# Enterprise Campus Network Lab 🖥️

A fully configured enterprise campus network built on two physical Cisco Catalyst 3850 switches, designed to simulate a real-world production environment.

<p align="center">
  <img width="931" alt="Enterprise Campus Network Lab topology: SWLAY3 Layer 3 core and SWLAY2 Layer 2 access switch joined by an LACP EtherChannel trunk" src="https://github.com/user-attachments/assets/12c3ce27-8476-4af8-a6f5-7b20a12321a0" />
</p>
<p align="center"><em>Lab topology: SWLAY3 (Layer 3 core) and SWLAY2 (Layer 2 access), connected by a two-link LACP EtherChannel trunk.</em></p>

## Network Overview
- **SWLAY3** — Layer 3 switch handling Inter-VLAN routing, DHCP, and ACL enforcement
- **SWLAY2** — Layer 2 switch handling all access port assignments and VLAN segmentation
- **Po1** — LACP EtherChannel uplink between both switches providing redundancy and 2Gbps aggregated bandwidth

## VLANs Configured
| VLAN | Name | Subnet |
|------|------|--------|
| 10 | Admin | 192.168.10.0/24 |
| 20 | ITS | 192.168.20.0/24 |
| 30 | Academic | 192.168.30.0/24 |
| 40 | VDI | 192.168.40.0/24 |
| 50 | Voice | 192.168.50.0/24 |
| 60 | Printer | 192.168.60.0/24 |
| 70 | AV | 192.168.70.0/24 |
| 80 | WiFi | 192.168.80.0/24 |
| 99 | Server | 192.168.99.0/24 |
| 100 | Management | 192.168.100.0/24 |

## Security Features
- **DHCP Snooping** — prevents rogue DHCP servers on all VLANs
- **Dynamic ARP Inspection (DAI)** — blocks ARP poisoning attacks by validating against the DHCP binding table
- **Port Security** — limits MAC addresses per port with inactivity-based aging
- **Extended ACLs** — enforces least-privilege traffic segmentation per VLAN

## ACL Policy Summary
- **WiFi** — internet access only, blocked from all internal VLANs and servers
- **Academic** — can reach servers, blocked from Admin and ITS
- **AV** — internet access only, blocked from Admin, ITS, and servers
- **Printer** — cannot initiate any traffic

## Configuration Files
Each file contains the full `show running-config` plus verification output (VLANs, trunks, EtherChannel, PoE, routing, DHCP snooping, DAI, and ACLs).

| Switch | Role | File |
|--------|------|------|
| SWLAY3 | Layer 3 core | [configs/Layer_3_switch_configuration.txt](configs/Layer_3_switch_configuration.txt) |
| SWLAY2 | Layer 2 access | [configs/Layer_2_switch_configuration.txt](configs/Layer_2_switch_configuration.txt) |

---
*Built as part of a personal home lab to reinforce enterprise networking concepts and prepare for CCNA certification.*
