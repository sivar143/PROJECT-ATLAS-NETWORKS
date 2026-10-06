# ATLAS Networks Global Power and Data Safety Architecture

## 1. Purpose

This is a mandatory cross-product hardware architecture rule for ATLAS Networks.

Every ATLAS hardware product shall be designed so that power and data interfaces have dedicated protection and sensing appropriate to the interface. Safety functions shall not depend solely on software.

This policy applies to routers, switches, mesh nodes, access points, security gateways and future ATLAS hardware platforms.

## 2. Mandatory power-line requirements

Every separately protected power branch shall include:

1. a fuse or resettable/electronic fuse appropriate to the rail;
2. voltage and current sensing;
3. over-current/short-circuit protection;
4. over-voltage/under-voltage protection where applicable;
5. controlled disconnect/isolation where practical;
6. fault telemetry to the system controller where practical.

The protection device shall be sized for normal operating current, startup/inrush, transient behavior, fault energy and thermal conditions. Fuse selection shall not be based only on nominal load current.

## 3. Mandatory power sensing

Power monitoring shall provide, as applicable:

- rail voltage;
- rail current;
- calculated power;
- over-current indication;
- under/over-voltage indication;
- abnormal consumption detection;
- thermal/fault status.

Critical protection must remain effective if the main processor or firmware is unavailable.

## 4. Mandatory data-interface safety

Every external and safety-critical data interface shall have an interface-appropriate protection/sensing path.

The implementation may include:

- ESD/surge protection;
- current/voltage/short detection where meaningful;
- interface power monitoring;
- fault detection;
- controlled isolation or shutdown;
- link/port fault telemetry.

For high-speed differential interfaces such as USB4, PCIe and multi-gigabit Ethernet, a conventional current-sense element must not be inserted into the high-speed signal path merely to satisfy this policy. Protection/sensing shall use an interface-appropriate device or architecture that preserves signal integrity, insertion loss, impedance and compliance margins.

Wi-Fi/RF paths shall use RF-appropriate protection and monitoring rather than electrical current sensing inserted into the RF path.

## 5. Active fault handling

Where the interface permits it, ATLAS hardware shall be able to:

1. detect a fault locally;
2. isolate or disable the affected branch/port;
3. report the fault;
4. recover automatically when safe, or require controlled restart;
5. keep unrelated interfaces operational.

A single failed port or branch should not unnecessarily disable the whole product.

## 6. Device-selection rules

Protection and sensing devices are part of the product architecture and BOM, not optional accessories.

Selection shall consider:

- latest production-qualified silicon meeting the product requirements;
- efficiency and quiescent power;
- current/voltage range;
- response time;
- fault behavior;
- thermal performance;
- interface bandwidth/SI impact;
- Linux/OpenWrt or firmware integration where telemetry is software-visible;
- lifecycle and supply availability;
- package and PCB constraints.

Preview, announcement-only or otherwise non-orderable silicon shall not be frozen as the production design.

## 7. Schematic and PCB implementation

For each product, the schematic shall explicitly show:

Power source -> fuse/protection -> sensing -> switching/regulation -> load

For applicable external data interfaces:

Connector -> ESD/surge/interface protection -> sensing/monitoring or protected switch -> PHY/controller

The exact topology shall be adapted to the interface and electrical requirements.

Protection and sensing placement shall be considered during PCB floorplanning so that fault energy is contained and high-speed signal integrity is maintained.

## 8. Firmware and telemetry

Where sensing devices expose digital telemetry, the software architecture shall provide:

- rail/port status;
- fault events;
- over-current/over-voltage events;
- protection trips;
- recovery status;
- diagnostic history.

Hardware protection remains authoritative; firmware telemetry and policy do not replace hardware protection.

## 9. Verification gate

No ATLAS hardware product is ready for schematic/PCB release until the applicable power and data safety paths have been reviewed.

Verification shall include:

- normal-load operation;
- startup/inrush;
- short-circuit/fault response;
- over-current response;
- over/under-voltage response where applicable;
- thermal operation;
- port isolation;
- recovery;
- high-speed SI impact;
- simultaneous-fault behavior where relevant.

## 10. Product-family applicability

| Product family | Power-line fuse/protection | Power sensing | Data-interface safety/sensing |
|---|---|---|---|
| X1 Lite | Mandatory | Mandatory | Mandatory |
| X1 | Mandatory | Mandatory | Mandatory |
| X1 Pro | Mandatory | Mandatory | Mandatory |
| Managed Switch | Mandatory | Mandatory | Mandatory |
| Enterprise Switch | Mandatory | Mandatory | Mandatory |
| Mesh Node | Mandatory | Mandatory | Mandatory |
| Access Point | Mandatory | Mandatory | Mandatory |
| Security Gateway | Mandatory | Mandatory | Mandatory |
| Other future ATLAS hardware | Mandatory | Mandatory | Mandatory |

## 11. Design interpretation

"Sense device for every data line" means every applicable data interface/port must have an appropriate safety/monitoring mechanism. It does not require placing a literal current-sense component in every individual high-speed differential pair.

The engineering objective is complete fault awareness and safe isolation without degrading the data interface.

This policy is a mandatory design gate for all future ATLAS hardware products.
