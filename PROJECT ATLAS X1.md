# PROJECT ATLAS X1
## Premium Wi-Fi 7 Home Router Platform
### Comprehensive Project Report (Version 2.0)

---

# Document Information

| Item | Details |
|------|---------|
| Project Name | ATLAS |
| Product Name | ATLAS X1 |
| Product Category | Premium Home Wi-Fi 7 Router |
| Document Version | 2.0 |
| Status | Engineering Concept |
| Target Software Support | 10 Years |
| Target Market | Premium Home / Prosumer |

---

# Executive Summary

Project ATLAS X1 is a premium next-generation home networking platform designed from the ground up with long-term reliability, high performance, maintainability, and security as its primary goals.

Unlike conventional consumer routers that prioritize cost, ATLAS X1 is engineered to deliver enterprise-inspired reliability while remaining simple enough for home users.

The platform introduces a dual independent operating system architecture, advanced thermal engineering, Wi-Fi 7, multi-gigabit networking, USB4 connectivity, and an intelligent software ecosystem designed for a minimum of ten years of firmware and security updates.

Project ATLAS is intended to become the foundation for an entire networking ecosystem, including future managed switches, access points, mesh systems, gateways, and cloud management software.

---

# Vision

To build one of the world's most reliable premium home networking platforms by combining:

- Long-term software support
- Premium hardware engineering
- Outstanding thermal performance
- Modern networking technologies
- Modular software architecture
- User-friendly management
- Professional-grade diagnostics

---

# Mission

Deliver networking products that remain secure, fast, reliable, and maintainable throughout a planned ten-year lifecycle without compromising user experience.

---

# Target Market

Primary Users

- Premium Home Users
- Gamers
- Content Creators
- Remote Workers
- Smart Home Owners
- Home Labs
- Small Offices

---

# Product Philosophy

ATLAS X1 is built around six core engineering principles:

1. Reliability
2. Security
3. Serviceability
4. Performance
5. Simplicity
6. Longevity

---

# Hardware Overview

## Processor

- Quad-Core 64-bit ARM Networking SoC
- Hardware NAT
- Hardware Crypto Engine
- Secure Boot Support
- PCIe Gen4
- High-Speed DMA Engine
- Hardware Packet Processing

---

## Memory

- 8 GB LPDDR4X / DDR4 (based on SoC compatibility)

---

## Storage

### System A

- 256 MB SPI NOR
- 4 GB NAND Flash

Contains:

- Bootloader
- Recovery
- Secure Keys
- AtlasOS
- Configuration
- Logs
- A/B Firmware Partitions

---

### System B

- 256 MB SPI NOR
- 4 GB NAND Flash

Contains:

- Bootloader
- Recovery
- Secure Keys
- OpenWrt
- Configuration
- Logs
- A/B Firmware Partitions

Both operating systems are completely independent.

No shared firmware partitions.

---

# Boot Architecture

Three-position hardware selector:

- AtlasOS
- Automatic
- OpenWrt

Each operating system boots only from its own SPI NOR and NAND.

Either operating system can recover the other.

---

# Networking Hardware

Wireless

- Wi-Fi 7
- Tri-Band
- 2.4 GHz
- 5 GHz
- 6 GHz
- Four High-Gain External Antennas

Planned support (subject to chipset capability and regulatory approval):

- Multi-Link Operation (MLO)
- 4096-QAM
- OFDMA
- MU-MIMO
- Beamforming
- Multi-RU
- Preamble Puncturing
- 320 MHz Channels
- WPA3
- EasyMesh (where supported)

---

Wired Networking

- 4 × 5 Gbps RJ45 LAN
- 2 × 10 Gbps SFP+ Ports
- Configurable WAN/LAN
- VLAN
- QoS
- Multi-WAN
- Link Aggregation (where hardware supports it)

---

USB Expansion

- 2 × USB4 Type-C

Supported Devices

- External SSD
- USB Ethernet
- Cellular Modems
- Diagnostic Devices
- Recovery Media
- Future Expansion Devices

---

# Security Architecture

Hardware

- Secure Boot
- Secure Element
- Firmware Verification
- Anti-Rollback Protection

Software

- WPA3-Personal
- WPA3-Enterprise (where supported)
- Stateful Firewall
- IPv6 Firewall
- WireGuard
- IPsec
- OpenVPN
- L2TP/IPsec
- DNS over HTTPS
- DNS over TLS
- MAC Filtering
- Device Quarantine
- Intrusion Detection / Prevention (hardware dependent)
- Automatic Security Updates

---

# Network Segmentation

AtlasOS supports multiple independent network profiles.

## Primary Network

Trusted devices

Examples

- PCs
- Laptops
- Phones
- Tablets
- NAS
- Gaming Consoles

---

## Guest Network

Features

- Internet-only access
- Client Isolation
- Time-Limited Access
- QR Code Sharing
- Independent QoS
- Independent Firewall Rules

---

## Dedicated IoT Network

A fully isolated smart-home network.

Features

- Separate SSID
- Dedicated VLAN/Subnet
- Independent DHCP
- Independent DNS
- Device Isolation
- Internet-only mode
- Independent Firewall
- Independent QoS
- Independent VPN
- Independent MAC Filtering
- Independent Content Policies
- Independent Bandwidth Limits

---

# Smart IoT Platform

AtlasOS shall provide:

- Automatic IoT device discovery
- One-click migration to IoT network
- Device categorization
- IoT Security Dashboard
- Fine-grained communication policies
- Firmware recommendations (where available)
- Device health overview
- Traffic monitoring
- Security recommendations

Examples

Allow:

- Phone → Smart Lights
- Tablet → Smart TV
- Home Assistant → IoT Devices

Block:

- IoT → Personal Computers
- Camera → NAS (unless permitted)
- IoT → IoT (optional)

---

# Software Platform

AtlasOS

Features

- Modern Web Interface
- Android Application
- iOS Application
- Secure Updates
- Automatic Firmware Rollback
- VPN
- Firewall
- VLAN
- QoS
- Diagnostics
- Device Management
- Multi-WAN
- USB Services

---

OpenWrt

Purpose

Advanced networking platform.

Features

- Package Management
- Development Environment
- Advanced Routing
- Experimental Features
- Community Ecosystem

---

# Intelligent Features

- Network Health Monitoring
- Automatic Diagnostics
- ISP Quality Testing
- DNS Performance Monitoring
- Wi-Fi Optimization
- Device Prioritization
- Application-Based QoS
- Long-Term Traffic History
- Automatic Security Recommendations

---

# Diagnostics

## OLED Display

Displays

- Boot Progress
- Active Operating System
- Internet Status
- CPU Usage
- Memory Usage
- Temperature
- Fan Speed
- Connected Clients
- Firmware Updates
- Recovery Progress
- Error Messages

---

## RGB Power Button

Functions

- Power Status
- Boot Progress
- Recovery
- Firmware Updates
- Hardware Diagnostics
- Error Codes

Error codes shall be documented on the official Atlas support website.

---

# Recovery System

Recovery functions

- Cross-flash AtlasOS
- Cross-flash OpenWrt
- Firmware Verification
- SPI NOR Recovery
- NAND Recovery
- Rollback
- Factory Reset
- Storage Diagnostics

No network recovery shall be required under normal recovery scenarios.

---

# Thermal Engineering

Objectives

- Quiet Operation
- Low Component Temperature
- Long Hardware Life
- Minimal Thermal Throttling

Airflow

Bottom filtered intake

↓

Large PWM cooling fan

↓

Primary Cooling Assembly

↓

Secondary Cooling Assembly

↓

Dual side exhaust

---

Cooling Materials

PTM7950 Phase-Change Thermal Interface Material

Primary Cooling Assembly

- CPU
- Ethernet Switch
- High-speed networking controllers

Secondary Cooling Assembly

- USB4 Controllers
- PMICs
- Supporting Controllers

Thermal zoning shall be validated through simulation and prototype testing.

---

# Mechanical Design

Material

Premium PC/ABS engineering plastic enclosure.

Features

- RF-transparent housing
- Replaceable dust filter
- Replaceable PWM fan
- Side exhaust vents
- Bottom filtered intake
- Internal structural frame
- Premium finish

---

# Serviceability

Replaceable Components

- Cooling Fan
- Dust Filter
- External Power Adapter

Service Features

- Accessible maintenance panel
- Built-in diagnostics
- Firmware recovery
- Hardware health monitoring

---

# Reliability Objectives

Designed for

- 10-Year Software Support
- Continuous 24×7 Operation
- Low Thermal Stress
- Firmware Rollback
- Independent Dual Operating Systems

---

# Estimated Investment (Preliminary)

Research & Development

₹17–18 Crore

Prototype Development

Included within R&D estimate

Initial Production (10,000 Units)

Approximately ₹48 Crore

Estimated Hardware BOM (Per Unit)

₹36,000–38,000

Estimated Manufacturing Cost (Per Unit)

₹45,000–50,000

Estimated Retail Price

₹65,000–75,000

(All figures are preliminary and subject to change based on final component selection, manufacturing volume, and market conditions.)

---

# Future Product Ecosystem

The ATLAS platform will expand into:

- ATLAS X1 Lite
- ATLAS X1
- ATLAS X1 Pro
- Managed Switches
- Enterprise Switches
- Mesh Wi-Fi Nodes
- Access Points
- Security Gateway
- Cloud Controller
- Mobile Applications
- Centralized Network Management Platform

All products will share a common software architecture wherever practical.

---

# Development Roadmap

Phase 1 — Product Definition ✅

Phase 2 — Hardware Architecture ✅

Phase 3 — Product Design Specification ✅

Phase 4 — Hardware Design Specification

Phase 5 — Component Selection

Phase 6 — Mechanical CAD Design

Phase 7 — Schematic Design

Phase 8 — PCB Layout

Phase 9 — Prototype Manufacturing

Phase 10 — Firmware Bring-up

Phase 11 — AtlasOS Development

Phase 12 — Mobile Applications

Phase 13 — Cloud Platform

Phase 14 — Compliance & Certification

Phase 15 — Mass Production

---

# Conclusion

Project ATLAS X1 is designed to redefine the premium home router category by combining enterprise-inspired engineering principles with a consumer-focused experience. Through physically isolated dual operating systems, robust recovery capabilities, advanced thermal management, Wi-Fi 7 connectivity, high-speed wired networking, USB4 expansion, and a ten-year software support strategy, the platform is intended to provide a durable foundation for a complete networking ecosystem.

Rather than being a single standalone product, ATLAS X1 serves as the cornerstone of the future ATLAS family of networking solutions, enabling a consistent software platform and user experience across routers, switches, access points, and cloud-managed infrastructure.
