# ATLAS X1 Engineering Design Package

## Purpose

This package converts the approved ATLAS X1 product concept and PDS into an engineering baseline suitable for detailed component selection and CAD/EDA work.

## Document map

1. ATLAS-X1-Hardware-Architecture.md — system partitioning and interfaces.
2. ATLAS-X1-Power-Architecture.md — power-tree requirements and protection.
3. ATLAS-X1-Boot-Storage-Recovery.md — dual-OS storage and recovery architecture.
4. ATLAS-X1-RF-Networking.md — Wi-Fi 7, Ethernet and RF architecture.
5. ATLAS-X1-USB4-Architecture.md — dual USB4 Type-C design requirements.
6. ATLAS-X1-Thermal-Mechanical.md — enclosure, airflow and thermal architecture.
7. ATLAS-X1-Security-Architecture.md — secure boot, keys and trust boundaries.
8. ATLAS-X1-PCB-Design-Rules.md — preliminary PCB/stack-up/layout rules.
9. ATLAS-X1-Manufacturing-Test.md — production test and provisioning strategy.
10. ATLAS-X1-Compliance-Plan.md — certification engineering plan.
11. ATLAS-X1-BOM-Framework.csv — engineering BOM structure.
12. ATLAS-X1-Block-Diagram.svg — editable system block diagram.
13. ATLAS-X1-Engineering-Verification-Plan.md — verification gates.

## Design maturity

- L0: concept
- L1: architecture frozen
- L2: component selection
- L3: schematic
- L4: PCB/mechanical design
- L5: EVT prototype
- L6: DVT
- L7: PVT / production release

Current target: L1 architecture baseline.

No document in this directory should be treated as a production release until its assumptions have been validated against selected silicon, reference designs, simulations and prototypes.
