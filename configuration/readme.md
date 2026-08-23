# CN Bank Network — Configuration Guide

This document details the device configuration steps used in the CN Bank Network Packet Tracer project. It covers switch, router, and server configuration in the order they were implemented.

---

## Prerequisites

- Cisco Packet Tracer installed
- `CN-Bank-Network.pkt` topology file open
- Basic familiarity with Cisco IOS CLI

---

## 1. Switch Configuration

### 1.1 Create VLANs

On each switch, VLANs were created to segment departments/services:

```
Switch> enable
Switch# configure terminal
Switch(config)# vlan <VLAN_ID>
Switch(config-vlan)# name <VLAN_NAME>
Switch(config-vlan)# exit
```

*(Repeat for each VLAN. Insert actual VLAN IDs/names from your design.)*

### 1.2 Assign Access Ports

Ports connected to end-user PCs and servers were set as access ports and assigned to their VLAN:

```
Switch(config)# interface <interface_id>
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan <VLAN_ID>
Switch(config-if)# exit
```

### 1.3 Configure Trunk Links

Links between switches, and between switch and router, were configured as trunks to carry multiple VLANs:

```
Switch(config)# interface <interface_id>
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk allowed vlan <VLAN_LIST>
Switch(config-if)# exit
```

### 1.4 Verification Commands

```
Switch# show vlan brief
Switch# show interfaces trunk
Switch# show running-config
```

---

## 2. Router Configuration

### 2.1 Sub-interfaces for Inter-VLAN Routing

*(If using router-on-a-stick)*

```
Router> enable
Router# configure terminal
Router(config)# interface <physical_interface>.<subinterface_number>
Router(config-subif)# encapsulation dot1Q <VLAN_ID>
Router(config-subif)# ip address <IP_ADDRESS> <SUBNET_MASK>
Router(config-subif)# exit
```

*(Repeat for each VLAN. Insert actual IPs once finalized.)*

### 2.2 Enable the Physical Interface

```
Router(config)# interface <physical_interface>
Router(config-if)# no shutdown
Router(config-if)# exit
```

### 2.3 Verification Commands

```
Router# show ip interface brief
Router# show ip route
Router# show running-config
```

---

## 3. Server Configuration

### 3.1 Banking Server

*(To be completed once finalized)*

- IP address: `<TBD>`
- Subnet mask: `<TBD>`
- Default gateway: `<TBD>`
- Services enabled: `<TBD>` (e.g. HTTP/HTTPS for a banking portal)

Steps in Packet Tracer:
1. Click the Banking Server device
2. Go to the **Desktop** tab → **IP Configuration** → enter static IP, subnet mask, and gateway
3. Go to the **Services** tab → enable required service(s)

### 3.2 DNS/DHCP Server

*(To be completed once finalized)*

**DHCP setup:**
1. Click the DNS/DHCP Server device
2. **Services** tab → **DHCP**
3. Configure pool name, default gateway, DNS server IP, start IP address, subnet mask, and max users per VLAN/segment
4. Turn service **On**

**DNS setup:**
1. **Services** tab → **DNS**
2. Add DNS records (hostname → IP mapping) for internal services (e.g. Banking Server)
3. Turn service **On**

**Client-side (PCs):**
- Set IP Configuration to **DHCP** on end-user PCs to receive dynamic addressing

---

## 4. Access Control Lists (ACLs)

*(To be completed)*

```
Router(config)# access-list <ACL_NUMBER> <permit/deny> <PROTOCOL> <SOURCE> <DESTINATION>
Router(config)# interface <interface_id>
Router(config-if)# ip access-group <ACL_NUMBER> <in/out>
```

Document each ACL's purpose here once implemented (e.g. restricting non-admin VLANs from reaching the Banking Server directly).

---

## 5. Verification & Testing Checklist

- [ ] `show vlan brief` confirms correct VLAN-to-port mapping
- [ ] `show interfaces trunk` confirms trunk links active with correct allowed VLANs
- [ ] `show ip route` confirms routes to all VLAN subnets
- [ ] PCs receive correct IP via DHCP
- [ ] DNS resolves Banking Server hostname correctly
- [ ] Ping/traceroute confirms expected connectivity between VLANs
- [ ] ACLs block/permit traffic as intended

---

## Notes

Replace all `<TBD>` and placeholder values with your actual VLAN IDs, IP addresses, and configuration details as they're finalized in the Packet Tracer file.
