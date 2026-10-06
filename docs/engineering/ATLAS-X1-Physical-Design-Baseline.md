# ATLAS X1 Physical Design Baseline

## Status

Integrated preliminary physical-design baseline for PCB, mechanical, RF and thermal CAD. This document is the coordination authority for the physical design until the selected platform and vendor reference designs are frozen.

## 1. Master coordinate system

- X: left to right when viewed from the front.
- Y: front to rear.
- Z: bottom to top.
- PCB origin: rear-left mechanical datum.
- All enclosure connector openings, PCB mounting holes and antenna mounting datums shall derive from the same master coordinate system.

## 2. Preliminary product envelope

| Item | Baseline |
|---|---|
| Enclosure | ~300 W × 190 D × 50–55 H mm |
| PCB | ~270 × 160 mm usable starting area |
| Main PCB | 8-layer routing baseline |
| External antennas | 4 |
| Cooling | Bottom filtered intake, forced-air fan, side exhaust |
| Service | Removable bottom/rear service access |

These dimensions are engineering starting values and are not a PDS change or tooling release.

## 3. Top-level physical partition

FRONT
+----------------------------------------------------------------+
| OLED / POWER BUTTON                                             |
|                                                                |
| RF / ANT C     Wi-Fi RF / FEM       RF / ANT D                 |
|                                                                |
| Storage / Security | SoC + DDR | USB4 / PCIe | Ethernet/PHY    |
|                    |           |              |                  |
|                    | PRIMARY HEATSINK / AIRFLOW                 |
|                                                                |
| ANT A                                            ANT B           |
+----------------------------------------------------------------+
REAR: SFP+ SFP+ 5GbE 5GbE 5GbE 5GbE USB4-A USB4-B DC-IN

The exact component coordinates shall be generated from the selected silicon reference layouts.

## 4. Physical zoning rules

### RF zone
Keep RF/FEM/antenna feeds away from:
- switching-regulator hot loops;
- Ethernet magnetics;
- fan motor/PWM wiring;
- USB4/PCIe clocks;
- DDR escape fields.

### Compute zone
SoC and DDR form one tightly coupled placement island.

### High-speed I/O zone
USB4, PCIe and Ethernet SerDes shall remain short, direct and connector-oriented.

### Power zone
Place DC input protection and conversion close to the power entry while keeping noisy switching nodes away from RF.

### Thermal zone
Highest-power components shall sit in the controlled fan/heatsink airflow corridor.

## 5. Mechanical/PCB interface control

The following coordinates shall be jointly owned:
- PCB outline;
- mounting holes;
- rear connector centers;
- USB-C shell/cutout centers;
- SFP cage openings;
- antenna connector centers;
- heatsink keepouts;
- fan mounting points;
- OLED window;
- power-button center.

Any change to these requires both PCB and mechanical review.

## 6. Antenna envelope

Four external antennas are arranged around the enclosure perimeter rather than clustered on one edge.

Baseline:
- A/B: rear corners;
- C/D: front/side corners.

The antenna mount shall permit controlled angular adjustment. Cable routing shall have defined bend radius and strain relief.

Final antenna separation, height, orientation and polarization shall be determined by the selected radio chain configuration and measured isolation.

## 7. Thermal/mechanical interface

Reserve:
- primary heatsink envelope over the highest-power compute/networking devices;
- secondary thermal pads/heatsinks where validated;
- fan intake plenum;
- exhaust plenum;
- filter pressure-drop volume.

No heatsink, shield or mechanical fastener may intrude into a vendor-required RF keepout.

## 8. Manufacturing/service features

Provide:
- accessible fan replacement;
- removable filter;
- PCB replacement path;
- connector retention;
- diagnostic access;
- controlled screw/boss locations;
- assembly datum features;
- captive or retained service fasteners where practical.

## 9. Physical design freeze conditions

Do not release detailed PCB routing or injection-molding tooling until:
1. platform/SoC is selected;
2. Wi-Fi reference design is selected;
3. Ethernet fabric is selected;
4. USB4 architecture is selected;
5. power tree is selected;
6. heatsink/fan envelope is validated;
7. antenna geometry is validated;
8. connector and mounting datums are frozen;
9. stack-up and impedance are approved.
