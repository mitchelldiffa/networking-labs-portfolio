LACP / Eth-Trunk Link Aggregation

Overview

This project demonstrates the configuration and verification of Link Aggregation Control Protocol (LACP) using Huawei switches in eNSP.

Two physical Ethernet links were bundled into a single logical Eth-Trunk interface between two switches. The lab also demonstrates link redundancy by testing the behavior of the aggregated link when one physical member link is disconnected.

Objectives

* Configure an Eth-Trunk interface on Huawei switches.
* Enable LACP using lacp-static mode.
* Add multiple physical interfaces to the Eth-Trunk.
* Verify LACP negotiation and member-port status.
* Demonstrate link redundancy and failover.
* Verify that the logical trunk remains operational when one physical link fails.

Lab Topology

The topology consists of two Huawei switches connected using two physical Ethernet links.

* SW1 GE0/0/1 ↔ SW2 GE0/0/1
* SW1 GE0/0/2 ↔ SW2 GE0/0/2
* Eth-Trunk ID: 1
* LACP mode: lacp-static

Configuration

SW1

system-view
sysname SW1
interface Eth-Trunk 1
mode lacp-static
interface GigabitEthernet 0/0/1
eth-trunk 1
interface GigabitEthernet 0/0/2
eth-trunk 1

SW2

system-view
sysname SW2
interface Eth-Trunk 1
mode lacp-static
interface GigabitEthernet 0/0/1
eth-trunk 1
interface GigabitEthernet 0/0/2
eth-trunk 1

Verification

The Eth-Trunk was verified using:

display eth-trunk 1

The verification showed:

* Eth-Trunk 1 operating status: UP
* Two member ports active
* GE0/0/1: Selected
* GE0/0/2: Selected
* LACP successfully established between the switches

Failover Test

One physical member link, GE0/0/2, was disconnected while the second link remained connected.

The Eth-Trunk remained operational with one active member port.

After reconnecting the physical link, both member ports returned to the Eth-Trunk.

This demonstrates the redundancy provided by link aggregation: the logical connection can remain operational when one physical member link becomes unavailable.

Skills Demonstrated

* Huawei VRP CLI
* Huawei eNSP
* Eth-Trunk configuration
* LACP
* Link aggregation
* Link redundancy
* Failover testing
* Network troubleshooting
* Configuration verification

Evidence

Topology

Eth-Trunk Configuration

LACP Verification

Failover Test

Key Takeaway

This lab demonstrates practical understanding of LACP-based link aggregation, including configuration, verification, and physical-link failure testing using Huawei eNSP.
