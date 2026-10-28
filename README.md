# Hotel Network Management using Cisco Packet Tracer

Design and simulation of the **Vic Modern Hotel** network in Cisco Packet Tracer, built as an end-of-year networking project. The network uses a hierarchical design across three floors, with inter-VLAN routing, OSPF, DHCP, SSH, port security, and wireless access.

## Topology

![Network Topology](images/topology.png)

## Project Overview

The hotel has three floors, with each department on its own VLAN and subnet:

| Floor | Department | VLAN | Network |
|-------|-----------|------|---------|
| 1st | Reception | 80 | 192.168.8.0/24 |
| 1st | Store | 70 | 192.168.7.0/24 |
| 1st | Logistics | 60 | 192.168.6.0/24 |
| 2nd | Finance | 50 | 192.168.5.0/24 |
| 2nd | HR | 40 | 192.168.4.0/24 |
| 2nd | Sales/Marketing | 30 | 192.168.3.0/24 |
| 3rd | Admin | 20 | 192.168.2.0/24 |
| 3rd | IT | 10 | 192.168.1.0/24 |

### Router Links (Serial DCE)

| Link | Network |
|------|---------|
| [Router1] to [Router2] | 10.10.10.0/30 |
| [Router2] to [Router3] | 10.10.10.4/30 |
| [Router1] to [Router3] | 10.10.10.8/30 |

## Features Implemented

- Hierarchical network design with 3 routers (one per floor) and 3 switches (one per floor)
- VLAN creation and port assignment for 8 departments
- Inter-VLAN routing using router-on-a-stick
- OSPF dynamic routing between all routers
- Router-based DHCP servers for PCs, printers, laptops, and phones
- Wireless LAN using Cisco access points on each floor
- SSH remote login on all routers
- Port security on the IT switch (sticky MAC, violation mode: shutdown) so only the Test-PC can use port Fa0/1
- Printers in every department
- Full end-to-end connectivity between all departments

## Tools Used

- Cisco Packet Tracer [version]

## How to Run

1. Install Cisco Packet Tracer.
2. Open `[filename].pkt` from this repository.
3. Wait for the links to turn green, then run the tests below.

## Testing and Verification

| Test | Method | Result |
|------|--------|--------|
| Connectivity between departments | `ping` between PCs in different VLANs | Successful |
| DHCP | Devices received IP addresses automatically | Successful |
| OSPF | `show ip route`, `show ip ospf neighbor` | Neighbors formed, routes learned |
| SSH | Remote login to routers from Test-PC | Successful |
| Port security | `show port-security interface fa0/1` | Sticky MAC learned, shutdown on violation |

Screenshots are in the `images/` folder.

## Repository Structure

```
├── [filename].pkt
├── images/
│   ├── topology.png
│   └── [test screenshots]
├── configs/          (optional: router and switch configurations)
└── README.md
```

## What I Learned

- Designing and subnetting a multi-VLAN network
- Configuring router-on-a-stick, OSPF, and DHCP on Cisco routers
- Securing remote access and switch ports
- Testing and troubleshooting network connectivity
