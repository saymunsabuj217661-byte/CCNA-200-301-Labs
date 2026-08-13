# CCNA 200-301 Practical Lab Documentation

## LAB 01 — Basic Cisco Switch Configuration

## 1. Objective

Configure a Cisco switch with basic initial configuration and access-security settings, then verify the configuration and Layer 2 connectivity using Cisco Packet Tracer.

## 2. Lab Environment

| Component | Details |
|---|---|
| Simulation Tool | Cisco Packet Tracer |
| Network Device | Cisco Switch |
| Switch Hostname | SW1 |
| Topology | PC0 — SW1 — PC1 |
| Layer | Layer 2 |

## 3. Network Topology

![Lab 01 Topology](topology.png)

## 4. Configuration Performed

- Configured the switch hostname as SW1.
- Configured an enable secret for privileged EXEC mode.
- Configured a Message of the Day (MOTD) banner: **"Authorized Users Only"**.
- Configured console-line password authentication.
- Enabled login on the console line.
- Enabled login on the VTY lines (0–4 and 5–15).
- Verified the switch running configuration.

## 5. Key Configuration Commands

```bash
enable
configure terminal
hostname sw1

enable secret <PASSWORD>

banner motd #Authorized Users Only#

line console 0
password <PASSWORD>
login
exit

line vty 0 4
login
exit

line vty 5 15
login
exit

Note: Passwords and encrypted secret values are intentionally omitted from the public documentation.

