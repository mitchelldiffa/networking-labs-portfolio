STP Redundancy & Root Bridge Selection

Project Overview

A hands-on networking lab built in Huawei eNSP to understand Spanning Tree Protocol (STP), redundant Layer 2 links, root bridge election, port roles, and STP reconvergence.

Objective

To build a redundant three-switch topology and observe how STP prevents Layer 2 loops by placing redundant paths into a non-forwarding state.

Network Topology

The lab consists of three Huawei switches connected in a triangle topology:

             SW1
            /   \
           /     \
         SW2─────SW3

This topology provides redundant paths between the switches.

Technologies & Skills

* Spanning Tree Protocol (STP)
* Root Bridge election
* Bridge Priority
* Root Port
* Designated Port
* Alternate Port
* Forwarding and Discarding states
* Network redundancy
* Loop prevention
* STP reconvergence
* Huawei VRP CLI

Initial STP State

The initial STP configuration was examined using:

display stp brief

The original topology had SW2 as the Root Bridge.

STP placed one redundant path into a non-forwarding state to prevent a Layer 2 loop.

Root Bridge Configuration

The STP priority on SW1 was changed to:

4096

This was configured using:

system-view
stp priority 4096

After the change, SW1 became the Root Bridge.

Verification

The STP topology was verified using:

display stp

and:

display stp brief

The verification showed that:

* SW1 became the Root Bridge.
* SW2 and SW3 selected their Root Ports toward SW1.
* The redundant path was placed into an Alternate/Discarding state.
* STP reconverged after the Root Bridge change.

What I Learned

This lab helped me understand how STP prevents switching loops while maintaining network redundancy.

I also learned how Bridge Priority influences Root Bridge election and how STP dynamically changes port roles when the network topology changes.

Tools Used

Huawei eNSP

Huawei VRP CLI
