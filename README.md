# Enterprise-Campus-Network-Lab
A fully configured enterprise campus network built on two physical Cisco Catalyst 3850 switches, designed to simulate a real-world production environment.
Network Overview

SWLAY2 — Layer 2 switch handling all access port assignments and VLAN segmentation
SWLAY3 — Layer 3 switch handling Inter-VLAN routing, DHCP, and ACL enforcement
Po1 — LACP EtherChannel uplink between both switches providing redundancy and 2Gbps aggregated bandwidth

VLANs Configured
VLANNameSubnet10Admin192.168.10.0/2420ITS192.168.20.0/2430Academic192.168.30.0/2440VDI192.168.40.0/2450Voice192.168.50.0/2460Printer192.168.60.0/2470AV192.168.70.0/2480WiFi192.168.80.0/2499Server192.168.99.0/24100Management192.168.100.0/24

Security Features
DHCP Snooping — prevents rogue DHCP servers on all VLANs
Dynamic ARP Inspection (DAI) — blocks ARP poisoning attacks by validating against the DHCP binding table
Port Security — limits MAC addresses per port with inactivity-based aging
Extended ACLs — enforces least-privilege traffic segmentation per VLAN

ACL Policy Summary

WiFi — internet access only, blocked from all internal VLANs and servers
Academic — can reach servers, blocked from Admin and ITS
AV — internet access only, blocked from Admin, ITS, and servers
Printer — cannot initiate any traffic

[Layer_2_switch_configuration.txt](https://github.com/user-attachments/files/26952601/Layer_2_switch_configuration.txt)
[Layer_3_switch_configuration.txt](https://github.com/user-attachments/files/26952629/Layer_3_switch_configuration.txt)


