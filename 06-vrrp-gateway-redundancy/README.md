VRRP Gateway Redundancy

Overview

This project demonstrates the configuration and verification of Virtual Router Redundancy Protocol (VRRP) using Huawei routers in eNSP.

Two routers were configured to provide a redundant default gateway for a host on the network. R1 operates as the initial VRRP Master, while R2 operates as the Backup router.

A failover test was performed by shutting down R1’s gateway interface. R2 successfully assumed the Master role while retaining the same virtual gateway address, allowing PC1 to continue reaching the virtual gateway.

Objectives

* Configure VRRP on two Huawei routers.
* Create a shared virtual gateway address.
* Configure Master and Backup router roles.
* Use VRRP priority to determine the preferred Master.
* Verify VRRP status and virtual IP information.
* Simulate router/interface failure.
* Verify automatic VRRP failover.
* Confirm gateway connectivity after failover.

Lab Topology

The lab consists of:

* 1 PC
* 1 Layer 2 switch
* 2 Huawei routers
* 1 VRRP virtual gateway

Addressing

Device	Interface	IP Address
PC1	Ethernet0/0/1	192.168.10.10/24
R1	GE0/0/0	192.168.10.2/24
R2	GE0/0/0	192.168.10.3/24
VRRP	Virtual IP	192.168.10.1/24

PC1 uses 192.168.10.1 as its default gateway.

VRRP Configuration

R1 — Master

system-view
sysname R1
interface GigabitEthernet 0/0/0
ip address 192.168.10.2 255.255.255.0
undo shutdown
vrrp vrid 1 virtual-ip 192.168.10.1
vrrp vrid 1 priority 120

R1 was configured with a higher priority of 120, making it the preferred VRRP Master.

R2 — Backup

system-view
sysname R2
interface GigabitEthernet 0/0/0
ip address 192.168.10.3 255.255.255.0
undo shutdown
vrrp vrid 1 virtual-ip 192.168.10.1
vrrp vrid 1 priority 100

R2 was configured with a priority of 100, making it the Backup router under normal conditions.

Verification

VRRP status was verified using:

display vrrp

The normal operating state was:

R1 → Master
R2 → Backup
Virtual IP → 192.168.10.1

Failover Test

To test gateway redundancy, the R1 gateway interface was temporarily shut down:

system-view
interface GigabitEthernet 0/0/0
shutdown

After R1 became unavailable, R2 transitioned from Backup to Master.

The virtual gateway remained:

192.168.10.1

PC1 was then used to verify that the virtual gateway remained reachable.

After the test, R1’s interface was restored using:

undo shutdown

R1 subsequently returned to the Master role because of its higher VRRP priority.

Skills Demonstrated

* Huawei eNSP
* Huawei VRP CLI
* VRRP
* Gateway redundancy
* Master/Backup router configuration
* VRRP priority
* Virtual IP configuration
* Network failover testing
* Connectivity verification
* Basic network troubleshooting

Evidence

Topology

R1 — VRRP Master

R2 — VRRP Backup

VRRP Failover

PC1 Connectivity After Failover

Key Takeaway

This lab demonstrates how VRRP provides default-gateway redundancy by allowing multiple routers to share a virtual gateway address.

The lab also demonstrates practical failover: when the active router became unavailable, the backup router assumed the Master role while the virtual gateway address remained unchanged.
