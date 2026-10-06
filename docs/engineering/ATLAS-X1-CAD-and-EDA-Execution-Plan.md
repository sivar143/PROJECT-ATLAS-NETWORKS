# ATLAS X1 CAD and EDA Execution Plan

## Purpose

Convert the current architecture into an executable schematic, PCB, mechanical CAD and prototype package without prematurely freezing unverified assumptions.

## 1. Required engineering artifacts

### Electrical
- system block diagram;
- complete power tree;
- complete clock/reset tree;
- SoC pin/lane map;
- DDR topology;
- Ethernet fabric schematic;
- USB4/Type-C schematic;
- RF/FEM schematic;
- storage/recovery schematic;
- secure-element schematic;
- monitoring/sensing architecture;
- fan/thermal controller;
- OLED/RGB/button circuitry;
- factory test interfaces.

### PCB
- approved stack-up;
- component placement;
- high-speed constraints;
- DDR constraints;
- PCIe Gen4 constraints;
- USB4 constraints;
- Ethernet SerDes constraints;
- RF 50-ohm constraints;
- power/ground strategy;
- DFM/DFT rules;
- Gerber/ODB++ manufacturing outputs after release.

### Mechanical
- master enclosure CAD;
- PCB mounting;
- antenna brackets;
- heatsinks;
- fan shroud;
- filter tray;
- connector cutouts;
- OLED window;
- service panel;
- fasteners;
- exploded assembly;
- tolerance stack.

### Simulation/validation
- SI;
- PI;
- thermal CFD;
- structural/interference;
- RF/antenna simulation;
- EMC pre-compliance;
- power integrity;
- worst-case power/thermal analysis.

## 2. CAD coordinate system

Define the master datum:
- X = left to right;
- Y = front to rear;
- Z = bottom to top.

Board origin shall be fixed relative to the rear connector datum.

Mechanical CAD and PCB CAD shall share the same connector datum and mounting-hole coordinate system.

## 3. PCB-to-mechanical ownership

PCB owns:
- connector centers;
- mounting holes;
- heatsink keepouts;
- antenna connector locations.

Mechanical assembly owns:
- enclosure surfaces;
- antenna articulation;
- fan/filter geometry;
- button/OLED openings;
- airflow baffles.

Changes affecting shared interfaces require cross-domain review.

## 4. Placement freeze sequence

1. Mechanical envelope.
2. Connector locations.
3. Antenna locations.
4. Fan/heatsink envelope.
5. SoC/DDR.
6. Ethernet.
7. USB4.
8. Power conversion.
9. Storage/security.
10. Test points.

## 5. Routing freeze sequence

1. DDR.
2. PCIe Gen4.
3. USB4.
4. Ethernet SerDes.
5. RF.
6. Clocks.
7. Lower-speed buses.
8. Power distribution.
9. Manufacturing/test access.

## 6. Mechanical freeze sequence

1. PCB envelope.
2. Connector cutouts.
3. Antenna mount.
4. Fan/filter.
5. Heatsink.
6. Airflow baffles.
7. Display/button.
8. Service panel.
9. Fasteners.
10. Enclosure cosmetic surfaces.

## 7. Engineering release gates

### Gate E0 — Architecture
All PDS requirements traced to hardware blocks.

### Gate E1 — Component selection
Production-qualified components selected and documented.

### Gate E2 — Schematic
ERC, power-tree review, safety review and reference-design review complete.

### Gate E3 — Placement
Mechanical interference, RF zoning, thermal zoning and high-speed escape complete.

### Gate E4 — Routing
SI/PI/DRC/DFM review complete.

### Gate E5 — Prototype
EVT bring-up, RF, thermal, power and interface testing complete.

### Gate E6 — DVT
Reliability, compliance and environmental testing complete.

No Gerber release shall occur before E4 approval.
