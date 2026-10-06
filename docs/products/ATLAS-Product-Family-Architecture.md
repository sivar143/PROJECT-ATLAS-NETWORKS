# ATLAS Product Family Architecture

## 1. Family principle

All ATLAS products shall share a common management model where practical:

- common device identity
- common secure provisioning
- common update/signing infrastructure
- common telemetry schema
- common diagnostics model
- common user/account model
- common site/network hierarchy
- common policy model
- common event/audit model
- common mobile/cloud APIs

Hardware remains product-specific.

## 2. Global hardware safety rule

All ATLAS hardware products shall implement the mandatory requirements in [ATLAS Global Power and Data Safety Architecture](../engineering/ATLAS-Global-Power-and-Data-Safety-Architecture.md).

At minimum, every separately protected power branch shall have appropriate fuse/protection and power sensing, and every applicable external or safety-critical data interface shall have interface-appropriate protection/sensing and fault handling. High-speed data paths must preserve signal integrity; this requirement does not mean inserting conventional current-sense elements into high-speed differential pairs.

These are architecture-level release gates and must be reflected in schematics, PCB floorplans, BOMs, firmware telemetry and verification plans.

## 3. Product matrix

| Product | Primary role | Connectivity focus | Management |
|---|---|---|---|
| X1 Lite | accessible premium router | Wi-Fi 7 + multi-gig Ethernet | local + optional cloud |
| X1 | flagship home/prosumer router | tri-band Wi-Fi 7 + 5GbE + 10GbE SFP+ + USB4 | local + optional cloud |
| X1 Pro | high-end router | higher aggregate throughput and expansion | local + cloud |
| Managed Switch | home/SOHO managed switching | 2.5/5/10GbE | local + cloud |
| Enterprise Switch | enterprise access/aggregation | high-density 1/2.5/5/10/25GbE | controller/cloud |
| Mesh Node | wireless extension | Wi-Fi 7 + Ethernet backhaul | X1/controller |
| Access Point | dedicated AP | Wi-Fi 7 + wired backhaul | controller/cloud |
| Security Gateway | routing/security | multi-WAN + high-speed firewall | local + cloud |
| Cloud Controller | fleet management | API/control plane | web/cloud |
| Mobile Apps | user administration | HTTPS/API | cloud/local pairing |

## 4. Common security model

Every managed hardware device should support:

1. device-unique identity;
2. secure boot where silicon supports it;
3. signed firmware;
4. anti-rollback;
5. secure update;
6. authenticated management;
7. audit logging;
8. factory provisioning;
9. recovery path.

## 5. Common software model

The hardware products should expose a consistent internal abstraction:

Device -> Interfaces -> Networks -> Policies -> Services -> Telemetry -> Events

This permits the mobile/cloud software to present a consistent experience while preserving hardware-specific capabilities.

## 6. Network hierarchy

The ecosystem should represent:

Organization
  -> Site
    -> Network
      -> Device
        -> Interface
        -> Client
        -> Policy
        -> Event

## 7. Interoperability

Products shall support standards-based networking rather than requiring an ATLAS-only topology. Proprietary management features must remain optional.

## 8. Lifecycle

All products should use a common lifecycle:

Concept -> Architecture -> Component selection -> Prototype -> Validation -> Certification -> Production -> Maintenance -> End-of-support

Power/data safety architecture review is required during architecture and component selection and again before schematic/PCB release.

## 9. Product-specific design files

Detailed hardware documents shall be created only when that product enters active engineering. This prevents premature component decisions and keeps the family architecture separate from fabrication data.
