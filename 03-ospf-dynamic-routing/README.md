OSPF Dynamic Routing with Huawei eNSP

Overview

This project demonstrates the configuration and verification of Open Shortest Path First (OSPF) dynamic routing using Huawei eNSP.

The lab consists of three routers and three PCs. OSPF is used to dynamically exchange routing information between the routers, allowing the PCs on different networks to communicate without manually configuring static routes.

Objectives

* Configure IP addressing on routers and PCs
* Configure OSPF on three Huawei routers
* Establish OSPF neighbor adjacencies
* Verify OSPF-learned routes
* Test end-to-end connectivity between different networks
* Save and verify the router configurations

Network Topology

IP Addressing

Device	Interface	IP Address	Network
R1	GE0/0/2	192.168.10.1/24	LAN 1
R1	GE0/0/0	10.0.12.1/30	R1-R2
R1	GE0/0/1	10.0.13.1/30	R1-R3
R2	GE0/0/1	10.0.12.2/30	R1-R2
R2	GE0/0/0	10.0.23.1/30	R2-R3
R2	GE0/0/2	192.168.20.1/24	LAN 2
R3	GE0/0/2	10.0.13.2/30	R1-R3
R3	GE0/0/0	10.0.23.2/30	R2-R3
R3	GE0/0/3	192.168.30.1/24	LAN 3

PC Addressing

PC	IP Address	Default Gateway
PC1	192.168.10.10/24	192.168.10.1
PC2	192.168.20.10/24	192.168.20.1
PC3	192.168.30.10/24	192.168.30.1

OSPF Configuration

OSPF process 1 was configured on all three routers using Area 0.

Router IDs:

* R1 — 1.1.1.1
* R2 — 2.2.2.2
* R3 — 3.3.3.3

OSPF was enabled on the router interfaces participating in the routing domain.

OSPF Neighbor Verification

The OSPF neighbor table was checked using:

display ospf peer brief

The routers successfully established OSPF neighbor relationships in the FULL state.

OSPF Routing Table

OSPF-learned routes were verified using:

display ip routing-table protocol ospf

R3 successfully learned the remote LAN networks:

* 192.168.10.0/24
* 192.168.20.0/24

Connectivity Verification

End-to-end connectivity was tested from PC3 to the remote networks.

PC3 successfully pinged:

ping 192.168.10.10
ping 192.168.20.10

Both tests were successful, confirming that traffic could travel between the different LANs through the OSPF-enabled routers.

Key Commands Used

display ospf peer brief
display ip routing-table protocol ospf
display ospf interface
display current-configuration
ping
save

Skills Demonstrated

* Huawei eNSP
* Huawei VRP
* OSPF
* Dynamic routing
* IPv4 addressing
* Router configuration
* OSPF neighbor verification
* Routing-table analysis
* Network troubleshooting
* End-to-end connectivity testing

Conclusion

This lab demonstrated how OSPF can dynamically exchange routing information between multiple routers. After configuring OSPF Area 0, all routers established neighbor relationships and learned remote networks dynamically. Successful end-to-end ping tests confirmed that the routing configuration was functioning correctly.
