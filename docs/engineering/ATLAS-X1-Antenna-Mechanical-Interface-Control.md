# ATLAS X1 Antenna Mechanical Interface Control

## Purpose

Define the mechanical interface between the four external antennas, enclosure and PCB before detailed antenna CAD.

## 1. Baseline

- Four external serviceable antennas.
- Broadband tri-band coverage for 2.4/5/6 GHz.
- Articulated or adjustable mounts.
- Connectorized coax feeds.
- No antenna element permanently bonded to the enclosure.

## 2. Locations

| Antenna | Baseline location | Initial orientation |
|---|---|---|
| A | rear-left corner | vertical |
| B | rear-right corner | vertical |
| C | front/left side | +45° |
| D | front/right side | -45° |

These are mechanical starting positions only.

## 3. Mechanical requirements

Each mount shall provide:
- defined rotational stops;
- repeatable attachment;
- connector strain relief;
- coax bend-radius control;
- resistance to repeated user adjustment;
- no interference with top/bottom enclosure panels;
- no interference with the fan airflow path.

## 4. RF isolation

Maintain the maximum practical physical separation between antennas.

The following must not be placed immediately adjacent to antenna radiators:
- metal heatsinks;
- SFP cages;
- RJ45 magnetics;
- fan motor;
- high-current DC wiring;
- display/control cables.

Final clearance is determined by antenna simulation and measurement.

## 5. Coax interface

Each path shall define:
- 50-ohm controlled impedance;
- connector type;
- cable length target;
- bend radius;
- retention point;
- ground/shield termination;
- assembly sequence.

## 6. Enclosure material

The antenna region shall use RF-transparent PC/PC-ABS or an equivalent qualified material.

Any metallic decorative feature near an antenna requires RF review.

## 7. Validation

Before mechanical antenna freeze:
- 3D interference check;
- antenna radiation simulation;
- S-parameter measurement;
- antenna-to-antenna isolation;
- enclosure material characterization;
- assembled-product OTA testing;
- regulatory pre-scan.

## 8. Change control

Changing antenna location, angle, enclosure material, coax length or nearby mechanical structure requires RF review because these changes can alter matching, efficiency and radiation pattern.
