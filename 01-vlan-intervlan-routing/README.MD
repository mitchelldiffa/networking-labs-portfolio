VLAN Segmentation & Inter-VLAN Routing

Project Overview

A hands-on networking lab built in Huawei eNSP to practice VLAN segmentation, 802.1Q trunking, and inter-VLAN routing using a Router-on-a-Stick configuration.

Objective

To configure a multi-switch network where devices are separated into different VLANs while allowing communication between VLANs through a router.

Network Topology

The lab consists of:

* 1 Huawei router
* 2 Huawei switches
* 4 PCs
* VLAN 10
* VLAN 20

Technologies & Skills

* VLAN configuration
* Access ports
* 802.1Q trunking
* Router-on-a-Stick
* Inter-VLAN routing
* IP addressing and subnetting
* Huawei VRP CLI
* Network troubleshooting
* Connectivity testing

Configuration

VLAN 10

* PC-A: 192.168.10.10/24
* PC-C: 192.168.10.20/24
* Default Gateway: 192.168.10.254

VLAN 20

* PC-B: 192.168.20.10/24
* PC-D: 192.168.20.20/24
* Default Gateway: 192.168.20.254

The router was configured with subinterfaces for VLAN 10 and VLAN 20 using 802.1Q VLAN termination.

Verification

Connectivity was tested using ICMP ping.

The following were successfully verified:

* Same-VLAN communication
* Inter-VLAN communication
* Router gateway reachability
* VLAN trunk connectivity

What I Learned

This project helped me understand how VLANs provide Layer 2 network segmentation and how a router can be used to enable communication between separate VLANs.

I also gained practical experience configuring and troubleshooting Huawei network devices using the VRP command-line interface.

Tools Used

Huawei eNSP

Huawei VRP CLI
