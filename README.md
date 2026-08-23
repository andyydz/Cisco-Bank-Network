# Cisco-Bank-Network

A simulated banking organization network built in **Cisco Packet Tracer** for a Computer Networks (CN) college group project. The goal is to design and configure a functional, reasonably secure network for a bank, covering topology design, VLAN segmentation, routing, server infrastructure, and access control.

## Project Overview

This project models the internal network infrastructure of a bank, including departmental segmentation, inter-VLAN routing, core banking services, and network security controls — implemented and tested entirely within Packet Tracer.

## Objectives

- Design a realistic, scalable network topology for a banking environment
- Segment departments/services using VLANs
- Enable secure inter-VLAN communication through routing
- Deploy core services (Banking Server, DNS/DHCP)
- Apply Access Control Lists (ACLs) to restrict/control traffic
- Test connectivity and validate network security

## Tech Stack / Tools

- Cisco Packet Tracer
- Cisco IOS (Router & Switch CLI configuration)

## Network Design

- **Topology:** Routers, switches, end-user PCs, and servers connected across multiple logical network segments
- **VLANs:** Used to logically separate departments/services within the bank
- **Trunking:** Configured between switches/routers to carry multiple VLANs over shared links
- **Routing:** Inter-VLAN routing configured to allow controlled communication between segments
- **Servers:** Dedicated Banking Server and DNS/DHCP Server for core services

> Detailed VLAN IDs, IP addressing, and subnetting are documented in [`docs/addressing-table.md`](docs/addressing-table.md) *(add this file once finalized).*

## Project Status

###  Completed
- [x] Physical/logical topology design
- [x] VLAN configuration
- [x] Switch port assignments (access ports)
- [x] Trunk configuration
- [x] Router configuration
- [x] Routing / inter-VLAN communication

###  In Progress
- [ ] Banking Server configuration
- [ ] DNS/DHCP Server configuration (dynamic IP allocation + hostname/domain resolution)

###  Planned
- [ ] Access Control Lists (ACLs)
- [ ] Connectivity testing
- [ ] Network security testing
- [ ] Final documentation & presentation

## Repository Structure

```
CN-Bank-Network/
├── README.md
├── packet-tracer/
│   └── CN-Bank-Network.pkt        # Main Packet Tracer file
├── docs/
│   ├── topology-diagram.png       # Network topology screenshot/export
│   ├── addressing-table.md        # VLANs, subnets, IPs, gateways
│   └── configs/                   # Exported device CLI configs
└── presentation/
    └── CN-Bank-Network.pptx       # Class presentation slides
```


## Getting Started

1. Install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer) (requires a free Cisco Networking Academy account)
2. Clone this repository
3. Open `packet-tracer/CN-Bank-Network.pkt`

## Course Context

This project was developed for a Computer Networks (CN) subject group assignment. It is separate from any individual Cisco Networking Academy / Network Defense coursework.

## License

Academic project — for educational purposes only.
