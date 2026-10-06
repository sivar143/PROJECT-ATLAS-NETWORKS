# ATLAS X1 PCB Design Rules — Preliminary

## 1. Status

These are architecture-stage rules. Final values must be derived from the selected PCB stack-up, fabricator capability and vendor reference designs.

## 2. Layering concept

Target a multilayer board sufficient for:

- dedicated ground planes
- power planes
- high-speed digital routing
- PCIe/USB4
- Ethernet SerDes
- DDR
- RF

A final layer count shall be chosen only after the lane count and routing density are known.

## 3. Floorplanning

Recommended zones:

1. SoC + DDR
2. Ethernet/SerDes
3. Wi-Fi/RF
4. USB4
5. power conversion
6. storage/security
7. user connectors

High-speed interfaces should be kept short and direct.

## 4. Grounding

- maintain continuous reference planes;
- minimize return-path discontinuities;
- avoid routing high-speed pairs across plane splits;
- use controlled stitching around RF and connector transitions.

## 5. DDR

DDR routing must follow the selected memory vendor/SoC reference design exactly for topology, impedance, length matching and timing constraints.

## 6. PCIe/USB4/SerDes

Use the selected vendor's channel-loss budget and stack-up calculations. Do not invent generic trace-width values before the fabricator stack-up is selected.

## 7. RF

Use controlled impedance and the radio vendor's recommended stack-up, keepout, via fence and antenna matching strategy.

## 8. Manufacturing

Provide:

- fiducials
- panelization constraints
- test points
- programming access
- assembly keepouts
- connector mechanical keepouts
- thermal/mechanical mounting features

## 9. DFM gate

Before PCB release:

- ERC clean
- DRC clean
- impedance calculation approved
- SI/PI review complete
- thermal review complete
- mechanical fit approved
- BOM lifecycle reviewed
- manufacturer DFM review complete
