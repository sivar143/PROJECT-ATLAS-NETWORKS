# ATLAS Product Family Design

This directory defines the product-level architecture for the ATLAS ecosystem identified in the ATLAS X1 project report.

The X1 is the engineering reference platform. Future products inherit common software, security, telemetry, provisioning, management and hardware-safety concepts but are not assumed to reuse the X1 PCB.

## Global hardware design policy

All ATLAS hardware products must follow:

- [ATLAS Global Power and Data Safety Architecture](../engineering/ATLAS-Global-Power-and-Data-Safety-Architecture.md)

This policy requires appropriate fuse/protection and sensing on protected power branches and interface-appropriate protection/sensing on applicable data interfaces, with active fault isolation where practical.

## Product design documents

- ATLAS-X1 — premium Wi-Fi 7 home/prosumer router; detailed engineering package in docs/engineering/.
- ATLAS-X1-Lite — value-oriented router derivative.
- ATLAS-X1-Pro — higher-performance router derivative.
- ATLAS-Managed-Switch — managed multi-gig switch family.
- ATLAS-Enterprise-Switch — enterprise switching platform.
- ATLAS-Mesh-Node — whole-home wireless expansion node.
- ATLAS-Access-Point — dedicated wired-backhaul Wi-Fi platform.
- ATLAS-Security-Gateway — security-first routing appliance.
- ATLAS-Cloud-Controller — centralized fleet/network management.
- ATLAS-Mobile-Apps — iOS/Android management clients.

The detailed X1 engineering package is the first hardware design to be advanced to component selection and EDA.
