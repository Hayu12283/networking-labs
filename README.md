# networking-labs
Osman Abdul-Hayudeen | Aspiring Network &amp; Computer Engineer  📍 Ghana | Building &amp; documenting enterprise networking architectures, CCNA-level routing/switching labs, and infrastructure builds.
# Enterprise Three-Tiered Hierarchy (Core, Distribution, Access)

## Architectural Overview
This project models a standard Cisco Three-Tiered Enterprise Network Architecture designed for high availability, fault tolerance, and deterministic traffic flow.

### Design Highlights:
* **Access Layer:** Layer 2 security hardening via Port Security, 802.1Q trunking, and native VLAN isolation.
* **Distribution Layer:** Inter-VLAN routing using Switched Virtual Interfaces (SVIs), First-Hop Redundancy Protocol (HSRP) active/standby gateways, and LACP EtherChannel aggregation.
* **Core Layer:** Ultra-fast, Layer 3 point-to-point routed links running OSPF Area 0 (Backbone) dynamic routing.

---

## Topology & Subnet Plan

| Subnet / Link | Network Range | Purpose |
| :--- | :--- | :--- |
| **VLAN 10** | `192.168.10.0/24` | Human Resources (Gateway: `192.168.10.1`) |
| **VLAN 20** | `192.168.20.0/24` | Information Technology (Gateway: `192.168.20.1`) |
| **VLAN 99** | `10.99.99.0/24` | In-Band Switch Management |
| **VLAN 666** | N/A | Native / Unused Port Isolation |
| **Core L3 Links** | `10.0.X.0/30` | Point-to-Point Inter-Switch Routing (OSPF Area 0) |

---

## Verification & Testing Commands

1. **Verify LACP EtherChannels:**
   ```bash
   show etherchannel summary
