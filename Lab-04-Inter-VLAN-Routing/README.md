
LAB 04 — Inter-VLAN Routing (Router-on-a-Stick)

1. Objective

Configure Inter-VLAN Routing using a Cisco router and two Layer 2 switches with the Router-on-a-Stick method.

This lab demonstrates communication between VLAN 10 and VLAN 20 using IEEE 802.1Q trunking and router subinterfaces.

2. Lab Environment

Component

Details

Simulation Tool

Cisco Packet Tracer

Router

Cisco PT Router

Switches

2 × Cisco 2960-24TT

VLANs

VLAN 10 and VLAN 20

Routing Method

Router-on-a-Stick

Trunk Protocol

IEEE 802.1Q

Network Layer

Layer 3

3. Network Topology



VLAN and IP Addressing

VLAN

Department

Network

Default Gateway

VLAN 10

HR

192.168.10.0/24

192.168.10.1

VLAN 20

IT

192.168.20.0/24

192.168.20.1

Device

VLAN

IP Address

Default Gateway

PC0

VLAN 10

192.168.10.10

192.168.10.1

PC2

VLAN 10

192.168.10.20

192.168.10.1

PC1

VLAN 20

192.168.20.10

192.168.20.1

PC3

VLAN 20

192.168.20.20

192.168.20.1

4. Configuration Performed

Configured VLAN 10 for HR.

Configured VLAN 20 for IT.

Assigned PC-facing ports to the appropriate VLANs.

Configured trunk links between the network devices.

Configured Router-on-a-Stick using router subinterfaces.

Configured IEEE 802.1Q encapsulation.

Configured default gateways for VLAN 10 and VLAN 20.

Verified VLAN and trunk configuration on both switches.

Verified router configuration.

Tested connectivity between devices in different VLANs.

5. Router-on-a-Stick Configuration

Physical Interface

interface GigabitEthernet0/0/0
 no ip address
 duplex auto
 speed auto

VLAN 10 Subinterface

interface GigabitEthernet0/0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0

VLAN 10 default gateway: 192.168.10.1

VLAN 20 Subinterface

interface GigabitEthernet0/0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0

VLAN 20 default gateway: 192.168.20.1

6. Switch Configuration

VLAN 10 Access Port

interface FastEthernet0/1
 switchport access vlan 10
 switchport mode access

VLAN 20 Access Port

interface FastEthernet0/2
 switchport access vlan 20
 switchport mode access

Trunk Ports

interface FastEthernet0/3
 switchport mode trunk

interface FastEthernet0/4
 switchport mode trunk

The trunk links carry VLAN 10 and VLAN 20 traffic between the switches and router.

7. Verification Commands

Verify Router Configuration

show running-config

Verify Router Interfaces

show ip interface brief

Verify VLANs

show vlan brief

Verify Trunk Configuration

show interfaces trunk

8. Verification Screenshots

Router Running Configuration



Trunk Running Configuration — Switch 1



Trunk Running Configuration — Switch 2



Trunk Verification — Switch 1



Trunk Verification — Switch 2



VLAN Verification — Switch 1



VLAN Verification — Switch 2



9. Connectivity Testing

Inter-VLAN connectivity was tested using ICMP.

Examples:

PC0 → PC1
192.168.10.10 → 192.168.20.10

PC1 → PC3
192.168.20.10 → 192.168.20.20

PC2 → PC0
192.168.10.20 → 192.168.10.10

The Packet Tracer connectivity test showed successful ICMP communication.



10. How Inter-VLAN Routing Works

VLAN 10 and VLAN 20 are separate Layer 2 broadcast domains.

The router provides Layer 3 communication between the two VLANs through subinterfaces:

VLAN 10
192.168.10.0/24
        |
        | 802.1Q
        |
G0/0/0.10
192.168.10.1
        |
      Router
        |
G0/0/0.20
192.168.20.1
        |
        | 802.1Q
        |
VLAN 20
192.168.20.0/24

The encapsulation dot1Q command identifies the VLAN associated with each router subinterface.

11. Expected Result

After completing the configuration:

VLAN 10 and VLAN 20 are configured.

PC-facing interfaces operate as access ports.

Trunk links carry VLAN 10 and VLAN 20 traffic.

Router subinterface G0/0/0.10 provides the gateway for VLAN 10.

Router subinterface G0/0/0.20 provides the gateway for VLAN 20.

IEEE 802.1Q encapsulation is configured.

Devices within the same VLAN can communicate.

Devices in different VLANs can communicate through the router.

Inter-VLAN routing works successfully.

12. Skills Demonstrated

Cisco IOS CLI

VLAN configuration

Access-port configuration

802.1Q trunking

Router-on-a-Stick

Router subinterfaces

Inter-VLAN routing

IP addressing

Default gateway configuration

Layer 2 and Layer 3 troubleshooting

Cisco Packet Tracer

Network verification

ICMP connectivity testing

13. Lab Files

File

Description

README.md

Lab documentation

Lab-04-Inter-VLAN-Routing-Router-on-a-Stick.pkt

Cisco Packet Tracer lab

topology.png

Network topology

router-running-config.png

Router running configuration

trunk-running-config.png

Switch 1 trunk configuration

trunk-running-config-sw2.png

Switch 2 trunk configuration

trunk-verification.png

Switch 1 trunk verification

trunk-verification-sw2.png

Switch 2 trunk verification

vlan-verification.png

Switch 1 VLAN verification

vlan-verification-sw2.png

Switch 2 VLAN verification

vlan-connectivity-test.png

VLAN/inter-VLAN connectivity test

CCNA 200-301

This lab is part of my CCNA 200-301 Practical Networking Lab Series.

Topics Covered

VLANs

802.1Q Trunking

Router-on-a-Stick

Inter-VLAN Routing

Router Subinterfaces

Default Gateways

Layer 2 Switching

Layer 3 Routing

Network Verification

Lab Status: COMPLETED