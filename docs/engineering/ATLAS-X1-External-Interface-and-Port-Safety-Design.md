# ATLAS X1 External Interface and Port Safety Design

## Status

Preliminary interface protection and fault-containment architecture.

## 1. Global rule

ATLAS X1 shall implement the global ATLAS Power and Data Safety Architecture.

Every separately protected power branch requires protection plus voltage/current sensing.

Every applicable external or safety-critical data interface requires interface-appropriate protection/monitoring and fault handling.

## 2. DC input

DC jack -> input fuse/eFuse -> surge/OV/UV protection -> voltage/current sensing -> main conversion

Requirements:
- reverse-polarity protection where applicable;
- over-voltage protection;
- over-current/short-circuit protection;
- input current/voltage telemetry;
- controlled system disconnect on catastrophic fault.

## 3. 5GbE RJ45 ports

RJ45 -> ESD/surge protection -> Ethernet PHY -> switch/fabric

Each port shall have:
- ESD protection;
- transient protection appropriate to connector environment;
- PHY fault monitoring;
- per-port link telemetry;
- per-port isolation/shutdown where supported;
- current sensing on any powered external Ethernet branch;
- magnetics selected for the PHY and compliance target.

No conventional current-sense element shall be inserted into high-speed differential Ethernet pairs.

## 4. SFP+ ports

Each SFP+ port shall include:
- connector/cage grounding strategy;
- ESD protection as required;
- module presence detection;
- module power protection;
- voltage/current monitoring;
- per-port power shutdown;
- temperature/fault telemetry where exposed;
- controlled SerDes path.

Module power shall be independently protected.

## 5. USB4 Type-C

Type-C -> ESD/CC protection -> PD/power switch -> VBUS sensing -> USB4 controller

Requirements:
- VBUS over-current protection;
- VBUS over-voltage protection;
- current/voltage sensing;
- CC protection;
- ESD protection;
- controlled discharge;
- per-port fault shutdown;
- cable/attach monitoring;
- thermal monitoring where practical.

Do not insert ordinary current sensors in USB4 differential pairs.

## 6. Antenna connectors

External antenna connectors shall be reviewed for:
- ESD exposure;
- mechanical retention;
- RF return loss;
- RF power handling;
- mismatch/VSWR monitoring where supported.

RF protection shall not compromise bandwidth or noise figure.

## 7. OLED/button/service interfaces

Internal display/control interfaces shall have:
- current-limited supply;
- ESD protection where user accessible;
- connector retention;
- fault isolation where practical.

## 8. Fault telemetry

Expose:
- DC input fault;
- power-rail fault;
- Ethernet port fault;
- SFP module power fault;
- USB-C port fault;
- fan fault;
- thermal fault;
- RF abnormal condition;
- protection trip count.

## 9. Hardware independence

Critical protection shall not depend solely on Linux/OpenWrt or AtlasOS being operational. Where supported, protection ICs shall autonomously disconnect a failed branch.

## 10. Validation

Test:
- short circuit;
- overload;
- hot-plug;
- ESD;
- surge/transient;
- connector fault;
- repeated recovery;
- thermal trip;
- sensor failure;
- CPU/MCU failure with active protection;
- simultaneous port faults.
