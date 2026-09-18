DHCP & DHCP Snooping

Overview

This project demonstrates the configuration of a Huawei router as a DHCP server and the implementation of DHCP Snooping on a Huawei switch to control and validate DHCP traffic.

The lab was built and tested using Huawei eNSP.

Topology

Devices:

* 1 Huawei Router (R1)
* 1 Huawei Switch (SW1)
* 2 PCs (PC1 and PC2)

Connections:

* R1 GE0/0/0 → SW1 GE0/0/1
* SW1 GE0/0/2 → PC1
* SW1 GE0/0/3 → PC2

IP Addressing

Device	Interface	IP Address
R1	GE0/0/0	192.168.50.1/24
PC1	—	DHCP
PC2	—	DHCP

DHCP Configuration

R1 was configured as the DHCP server using the 192.168.50.0/24 network.

DHCP parameters included:

* Gateway: 192.168.50.1
* Subnet Mask: 255.255.255.0
* DNS Server: 8.8.8.8

PC1 and PC2 were configured to obtain their IPv4 addresses automatically through DHCP.

DHCP Snooping Configuration

DHCP Snooping was enabled on SW1 to help protect the network from unauthorized DHCP servers.

The interface connected to the legitimate DHCP server was configured as trusted:

* GE0/0/1 → R1 — Trusted

The interfaces connected to the clients remained untrusted:

* GE0/0/2 → PC1 — Untrusted
* GE0/0/3 → PC2 — Untrusted

Verification

After DHCP Snooping was enabled:

* PC1 received 192.168.50.254
* PC2 received 192.168.50.253
* Both PCs received the correct subnet mask and gateway.
* PC1 successfully pinged the gateway 192.168.50.1.
* PC2 successfully pinged the gateway 192.168.50.1.
* DHCP continued to operate after DHCP Snooping was enabled.

Evidence

Topology

DHCP Pool Configuration

DHCP Snooping Configuration

PC1 DHCP Configuration

PC2 DHCP Configuration 

Connectivity Test

Skills Demonstrated

* DHCP Server Configuration
* DHCP Address Allocation
* DHCP Snooping
* Trusted and Untrusted Switch Ports
* IPv4 Addressing
* Network Connectivity Testing
* Huawei eNSP
* Basic Network Security
* Network Troubleshooting
