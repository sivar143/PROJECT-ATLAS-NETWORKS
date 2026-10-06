# ATLAS X1 PCB Stack-Up and Placement Design

## Status

Preliminary PCB engineering baseline. Final stack-up shall be released by the PCB fabricator after SI/PI and impedance calculations.

## 1. Board concept

Target:
- large multi-layer main PCB;
- controlled-impedance high-speed routing;
- dedicated solid reference planes;
- separated power distribution regions;
- RF keepout/quiet zone;
- edge-mounted connectors;
- service/debug access.

## 2. Preliminary stack-up

Use an 8-layer baseline for initial routing studies:

| Layer | Function |
|---|---|
| L1 | Components + RF + critical signals |
| L2 | Solid GND reference |
| L3 | High-speed signals |
| L4 | Power planes / lower-speed signals |
| L5 | Solid GND reference |
| L6 | High-speed signals |
| L7 | Power / lower-speed signals |
| L8 | Components + signals |

This is a routing-study baseline, not a manufacturing stack-up. If DDR, PCIe Gen4 or USB4 cannot be routed with adequate margin, increase layer count rather than compromising electrical requirements.

## 3. Controlled impedance

Initial targets:
- 50-ohm single-ended RF;
- 90-ohm differential USB4/PCIe class routing, subject to controller and fabricator specification;
- Ethernet SerDes impedance per PHY/switch vendor;
- DDR impedance and topology exactly per memory-controller vendor.

The fabricator shall provide an impedance coupon plan.

## 4. Major placement zones

Recommended board partition:

[RF / Wi-Fi] [SoC + DDR] [USB4] [Ethernet / SFP] [POWER]

The partition shall be optimized around final connector locations and airflow.

## 5. SoC + DDR

The SoC and DDR are the highest-priority placement group:
- DDR immediately adjacent to SoC;
- shortest feasible byte-lane/address/control routes;
- matched topology per SoC vendor;
- no connector or mounting feature through DDR escape field;
- high-current power planes directly below/near SoC power entry.

## 6. Ethernet

Place:
- switch/fabric close to SoC/fabric interface;
- 5GbE PHYs between switch and RJ45;
- magnetics as close as practical to RJ45;
- SFP cages at board edge;
- SFP SerDes directly between switch/PHY architecture and cages.

Avoid routing Ethernet SerDes through RF zones.

## 7. USB4

Place the USB4 host controller between the PCIe Gen4 host source and the two Type-C connectors.

The PCIe Gen4 x4 path shall be short and direct.

Each Type-C port shall have:
- dedicated power protection;
- VBUS current/voltage monitoring;
- ESD protection;
- CC/PD protection;
- controlled discharge;
- per-port fault isolation.

Do not insert ordinary current-sense elements in USB4 differential pairs.

Retimers/redrivers shall be populated only if channel analysis proves they are required.

## 8. Power placement

Partition:
1. DC input protection/sensing;
2. high-current core rails;
3. memory rails;
4. RF rails;
5. Ethernet rails;
6. USB4/Type-C rails;
7. storage/security/UI rails;
8. fan/auxiliary rails.

Each separately protected branch shall implement the global ATLAS power/data safety architecture.

Keep switching hot loops compact and away from RF.

## 9. Storage/security

Keep the two boot/storage domains physically separable:
- AtlasOS NOR/NAND;
- OpenWrt NOR/NAND;
- secure element;
- boot/recovery controller.

The secure element should not share an uncontrolled power domain with an external connector.

## 10. Thermal placement

Place the highest dissipation components along:

FAN -> SoC/SWITCH/PHY HEATSINK -> SIDE EXHAUST

USB4 and PMIC hot spots shall occupy the secondary airflow region.

## 11. Display/control

OLED and button/controller shall be at the front edge. Keep display clocks and LED PWM away from antenna feeds.

## 12. Test points

Provide manufacturing/service test points for:
- main input voltage/current;
- major power rails;
- reset;
- boot selection;
- UART;
- JTAG/secure debug;
- SPI NOR A/B;
- NAND A/B;
- Ethernet;
- USB4;
- fan PWM/tach;
- temperature sensors.

## 13. Design-for-test

Where practical include:
- boundary scan/JTAG;
- boot straps;
- factory Ethernet loopback;
- USB4 compliance/test access;
- RF conducted test connectors before the final RF connector stage;
- power-rail measurement points.

## 14. PCB safety and isolation

Every external interface shall be reviewed for:
- ESD;
- surge/transient exposure;
- over-current;
- over-voltage;
- fault containment;
- sensing;
- controlled shutdown.

High-speed differential links shall not be degraded by inappropriate protection/sense components.

## 15. PCB release gates

Release to detailed routing only after:
- selected silicon pinout frozen;
- DDR topology frozen;
- PCIe lane map frozen;
- Ethernet architecture frozen;
- USB4 architecture frozen;
- RF platform frozen;
- power tree frozen;
- stack-up impedance approved;
- mechanical envelope approved.
