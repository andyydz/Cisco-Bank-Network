# CN Bank Network — Security Documentation

This document outlines the security design, controls, and testing approach for the CN Bank Network project. As a simulated banking network, security is a core focus alongside standard connectivity.

---

## 1. Security Objectives

- Restrict access between departments/segments to only what is necessary
- Protect the Banking Server from unauthorized access
- Prevent unauthorized devices from obtaining network access or spoofing services
- Ensure only intended traffic can reach sensitive segments
- Validate that security controls work through explicit testing (not just assumed)

---

## 2. Network Segmentation (First Line of Defense)

VLANs separate departments/services so that a compromise or misuse in one segment doesn't automatically expose others. This segmentation is the foundation the ACLs below build on.

| VLAN/Segment | Sensitivity | Notes |
|--------------|-------------|-------|
| — | — | *(Fill in — e.g. Admin/Management = high, Customer Service = medium, Servers = high, Guest = low)* |

---

## 3. Access Control Lists (ACLs)

ACLs enforce which segments can talk to which, and over what protocols.

### 3.1 ACL Policy Table

| ACL Name/Number | Applied On | Direction | Source | Destination | Action | Purpose |
|------------------|------------|-----------|--------|--------------|--------|---------|
| — | — | — | — | — | — | *(e.g. Deny Guest VLAN → Banking Server; Permit Admin VLAN → Banking Server on HTTP/HTTPS)* |

### 3.2 Design Principles Applied
- **Least privilege:** Only permit traffic explicitly required; deny by default
- **Sensitive segment isolation:** Only authorized VLANs (e.g. Admin) can reach the Banking Server
- **Explicit deny logging (if supported):** Track denied attempts for review

*(Fill in actual ACL rules once configured in Packet Tracer, including the `access-list` and `ip access-group` commands used.)*

---

## 4. Server-Side Security Considerations

### 4.1 Banking Server
- Only necessary services enabled (avoid running unused services that expand attack surface)
- Access restricted via ACL to authorized VLANs only
- *(Add authentication details if configured, e.g. login required for any hosted portal)*

### 4.2 DNS/DHCP Server
- DHCP scope limited to expected address ranges per VLAN, reducing risk of unauthorized/rogue devices being served large or unintended pools
- DNS records restricted to internal, known hostnames

---

## 5. Threats Considered

| Threat | Mitigation |
|--------|------------|
| Unauthorized cross-department access | VLAN segmentation + ACLs |
| Unauthorized access to Banking Server | ACL restricting source VLANs |
| Rogue device obtaining IP/network access | DHCP scope control per VLAN |
| Traffic sniffing across departments | VLAN separation limits broadcast domain exposure |
| Misconfigured trunk exposing VLANs | Explicit `switchport trunk allowed vlan` restriction to only required VLANs |

*(Expand this table with any additional threats your team specifically discussed or tested.)*

---

## 6. Security Testing

### 6.1 Test Plan

| Test | Expected Result | Actual Result | Status |
|------|------------------|----------------|--------|
| PC in Guest VLAN pings Banking Server | Denied | — |  Planned |
| PC in Admin VLAN pings Banking Server | Permitted | — |  Planned |
| PC in unauthorized VLAN attempts HTTP access to Banking Server | Denied | — |  Planned |
| DHCP request from within expected VLAN | IP assigned from correct pool | — |  Planned |
| Unauthorized VLAN attempts DNS query for internal hostname | *(Define expected behavior)* | — |  Planned |

Fill in "Actual Result" and "Status" ( Pass /  Fail) as tests are run in Packet Tracer, using `ping`, `tracert`, and simulation mode (packet capture) to confirm ACL enforcement.

### 6.2 Evidence
- Screenshots of successful/blocked pings
- `show access-lists` output showing match counters
- Packet Tracer Simulation Mode captures showing ACL drops

*(Reference screenshot files here once added, e.g. `docs/security-tests/`)*

---

## 7. Known Limitations

- This is a simulated environment (Packet Tracer) — does not include real-world protections such as firewalls, IDS/IPS, encryption in transit, or authentication servers (e.g. RADIUS/AAA), unless explicitly added
- ACLs are the primary security control in this project; no host-based security is modeled

---

## 8. Future Improvements (Optional/Stretch Goals)

- Port security on access ports (restrict MAC addresses per port)
- DHCP snooping to prevent rogue DHCP servers
- AAA/RADIUS authentication for device/console access
- Syslog server for centralized logging of denied traffic

---

## Notes

Replace all placeholder rows and `<TBD>` markers with your actual VLAN sensitivity levels, ACL rules, and test results as they're finalized in the Packet Tracer file.
