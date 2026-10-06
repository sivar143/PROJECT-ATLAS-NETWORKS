# ATLAS X1 Mechanical Enclosure Design

## Status

Preliminary mechanical architecture — L1/L2 engineering baseline. This document defines the enclosure concept and interfaces for CAD development. It does not replace the PDS.

## 1. Mechanical objectives

The enclosure shall:
- support the PDS four external Wi-Fi antennas;
- provide bottom filtered intake and dual-side exhaust;
- support a large PWM-controlled serviceable fan;
- keep RF regions clear of major digital/power noise sources;
- provide a rigid internal frame for the PCB, heatsinks and antenna mounts;
- permit fan/filter service without replacing the complete chassis;
- protect all external connectors against mechanical loading;
- provide controlled airflow through the thermal stack;
- remain RF-transparent around the antenna operating zones.

## 2. Preliminary envelope

Use this as a CAD starting envelope, not a frozen PDS dimension:

| Parameter | Preliminary target |
|---|---:|
| Main body width | 300 mm |
| Main body depth | 190 mm |
| Main body height | 50–55 mm |
| PCB usable area | ~270 × 160 mm |
| Bottom intake zone | ≥70% of available bottom area where structurally possible |
| Side exhaust | Two longitudinal exhaust zones |
| Service panel | Bottom/rear removable panel |
| Antenna mount height | Above the RF/digital PCB plane |

Final dimensions shall be driven by selected silicon, RF reference design, connector stack, fan, heatsink and antenna assembly.

## 3. Enclosure stack

1. RF-transparent PC/PC-ABS outer shell.
2. Internal structural frame.
3. PCB standoffs.
4. Airflow baffle/shroud around the main heatsink.
5. Replaceable bottom dust filter.
6. Serviceable fan module.
7. Antenna mounting bosses isolated from the PCB where practical.

Do not create a continuous conductive enclosure around the RF antenna field unless the antenna design explicitly requires it.

## 4. Connector face

Baseline rear arrangement:

[SFP+] [SFP+] [5GbE] [5GbE] [5GbE] [5GbE] [USB4-A] [USB4-B] [DC IN]

Final ordering may be optimized after PCB routing and thermal analysis. All high-speed connectors shall remain at the board edge.

Provide mechanical strain relief for DC input and retention features for USB-C and SFP cages.

## 5. PCB mounting

- controlled-height standoffs;
- no standoff through RF keepout;
- no mounting screw through high-speed differential routing corridors;
- defined connector alignment tolerances;
- PCB removable without destroying antenna hardware;
- defined grounding points for intentionally bonded conductive parts.

## 6. Airflow

Baseline:

BOTTOM FILTERED INTAKE -> FAN -> PRIMARY HEATSINK -> SECONDARY THERMAL ZONE -> DUAL SIDE EXHAUST

The airflow path shall be physically guided rather than relying on unrestricted convection.

## 7. Antenna mounting

Four external antennas shall use robust coax interfaces.

Baseline:
- A: rear-left;
- B: rear-right;
- C: front/side-left;
- D: front/side-right.

The final antenna angle shall be adjustable. At least two antenna assemblies should support different physical polarization orientations so MIMO performance is not dominated by one polarization.

## 8. OLED and controls

The front OLED shall have a dedicated optical window. The power/RGB button shall be mechanically isolated from the display.

## 9. Acoustic design

Fan control shall use PWM, tachometer feedback, temperature control, startup validation and stall detection.

Use elastomeric fan isolation where practical. Avoid large uninterrupted plastic panels directly over the fan.

## 10. Serviceability

The service panel shall expose the fan, filter and appropriate diagnostic/test access. The PCB should remain replaceable without destroying the enclosure. No adhesive-only attachment shall be used for service-critical components.

## 11. Mechanical validation

Before tooling:
- 3D CAD interference check;
- connector tolerance stack;
- antenna articulation envelope;
- fan/filter replacement procedure;
- thermal airflow CFD;
- antenna/cavity simulation;
- EMC/current-return review;
- screw-boss stress analysis;
- DFM/DFA review.
