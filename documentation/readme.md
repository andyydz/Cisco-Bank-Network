# CN Bank Network — Technical Documentation

This document provides detailed technical documentation for the CN Bank Network project, a simulated banking organization network built in Cisco Packet Tracer for a Computer Networks (CN) college group assignment.

---

## 1. Introduction

### 1.1 Purpose
To design and implement a functional, segmented, and reasonably secure network infrastructure representing a banking organization, demonstrating core networking concepts: topology design, VLAN segmentation, trunking, routing, server services, and access control.

### 1.2 Scope
The project covers the full lifecycle of network design for a simulated bank: physical/logical topology, Layer 2 segmentation (VLANs, trunking), Layer 3 routing (inter-VLAN communication), core network services (DNS/DHCP, banking application server), and security controls (ACLs), followed by connectivity and security testing.

### 1.3 Tools Used
- Cisco Packet Tracer
- Cisco IOS CLI (router and switch configuration)

---

## 2. Network Architecture

### 2.1 Topology Overview
The network consists of Cisco routers, Cisco switches, end-user PCs, and server infrastructure, connected across multiple logical network segments representing different departments/services within the bank.

*(Insert topology diagram here — export from Packet Tracer as PNG and reference it, e.g. `docs/topology-diagram.png`)*

### 2.2 Devices

| Device | Role |
|--------|------|
| Router | Inter-VLAN routing, gateway between segments |
| Switch(es) | VLAN segmentation, access port assignment, trunking |
| End-user PCs | Represent department workstations |
| Banking Server | Hosts internal banking service/application |
| DNS/DHCP Server | Provides dynamic IP allocation and name resolution |

*(Add specific device names/models as used in your Packet Tracer file, e.g. Router0 = 2911, Switch0 = 2960, etc.)*

---

## 3. VLAN Design

VLANs are used to logically separate departments/services within the bank network (e.g. administration, customer service, servers, etc.).

| VLAN ID | VLAN Name | Purpose | Assigned Ports |
|---------|-----------|---------|-----------------|
| — | — | — | — |

*(Fill in your actual VLAN table here.)*

---

## 4. IP Addressing Scheme

| VLAN/Segment | Network Address | Subnet Mask | Gateway | DHCP Range |
|--------------|------------------|-------------|---------|------------|
| — | — | — | — | — |

*(Fill in your actual addressing table here.)*

---

## 5. Switch Configuration

### 5.1 VLAN Configuration
VLANs created and assigned per department/service segment (see Section 3).

### 5.2 Access Port Assignment
End-user and server-facing ports configured as access ports and assigned to their respective VLANs.

### 5.3 Trunk Configuration
Trunk links configured between switches and between switch-to-router (router-on-a-stick or Layer 3 switch, as applicable) to carry multiple VLANs over shared links.

*(Paste relevant `show vlan brief` / `show interfaces trunk` output or config snippets once available.)*

---

## 6. Router Configuration

### 6.1 Routing Method
Inter-VLAN routing implemented to allow controlled communication between segments.

*(Specify method: router-on-a-stick with subinterfaces, or Layer 3 switching — fill in once confirmed.)*

### 6.2 Routing Table
*(Paste `show ip route` output once available.)*

---

## 7. Server Configuration

### 7.1 Banking Server
Represents an internal banking service/application within the network.

- **Services hosted:** *(TBD)*
- **IP configuration:** *(TBD)*
- **VLAN/Segment:** *(TBD)*

### 7.2 DNS/DHCP Server
- **DHCP:** Provides dynamic IP address allocation to end devices per VLAN/segment
- **DNS:** Provides hostname/domain resolution for internal services
- **IP configuration:** *(TBD)*

---

## 8. Access Control Lists (ACLs)

*(To be completed — document ACL rules once configured, e.g. restricting which VLANs can reach the Banking Server, blocking unauthorized inter-department traffic, etc.)*

| ACL Name/Number | Applied On | Direction | Purpose |
|------------------|------------|-----------|---------|
| — | — | — | — |

---

## 9. Testing & Validation

### 9.1 Connectivity Testing
*(To be completed — document ping/traceroute tests between VLANs, PC-to-server, etc.)*

### 9.2 Security Testing
*(To be completed — document tests validating ACL enforcement, e.g. denied traffic confirmations.)*

---

## 10. Project Status Summary

| Stage | Status |
|-------|--------|
| Physical/logical topology |  Completed |
| VLAN configuration |  Completed |
| Switch port assignments |  Completed |
| Trunk configuration |  Completed |
| Router configuration |  Completed |
| Routing / inter-VLAN communication |  Completed |
| Banking Server configuration |  In Progress |
| DNS/DHCP Server configuration |  In Progress |
| ACL configuration |  Planned |
| Connectivity testing |  Planned |
| Security testing |  Planned |

---

## 11. References

- Cisco Packet Tracer official documentation
- Course materials from Computer Networks subject
-
