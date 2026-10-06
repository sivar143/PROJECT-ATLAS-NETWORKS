# Product Design Specification (PDS)

## Project Name

**Project ATLAS X1**

---

# Document Information

| Item | Value |
|------|-------|
| Project | ATLAS X1 |
| Product Type | Premium Home Wi-Fi 7 Router |
| Version | PDS v1.0 |
| Status | Concept Design |
| Target Support Lifecycle | 10 Years |

---

# 1. Product Vision

Develop a premium home Wi-Fi 7 router that combines:

- Enterprise-inspired reliability
- Consumer-friendly operation
- Long-term software support
- Outstanding thermal performance
- Excellent repairability
- Dual operating systems
- High-speed networking

The product shall remain relevant throughout a 10-year software support lifecycle while maintaining high performance and reliability.

---

# 2. Target Customers

- Premium home users
- Enthusiasts
- Gamers
- Smart home users
- Content creators
- Home laboratories
- Small office / home office

---

# 3. Primary Objectives

The router shall:

- Support Wi-Fi 7
- Support dual operating systems
- Operate reliably for 10 years
- Allow independent firmware recovery
- Provide premium thermal management
- Support high-speed wired networking
- Deliver quiet operation
- Support future software expansion

---

# 4. Hardware Requirements

## Processor

- Quad-core ARM 64-bit networking SoC
- Hardware NAT
- Hardware cryptographic acceleration
- Secure Boot support
- PCIe Gen4
- High-speed DMA engine
- Integrated networking acceleration

---

## Memory

- 8 GB DDR4 or LPDDR4X (final choice based on SoC compatibility)

---

## Storage

### Storage System A

- SPI NOR #1
  - 256 MB
  - Bootloader
  - Recovery Image
  - Secure Boot Keys

- NAND #1
  - 4 GB
  - Custom Router OS
  - Configuration
  - Logs
  - A/B Firmware Partitions

---

### Storage System B

- SPI NOR #2
  - 256 MB
  - Bootloader
  - Recovery Image
  - Secure Boot Keys

- NAND #2
  - 4 GB
  - OpenWrt
  - Configuration
  - Logs
  - A/B Firmware Partitions

---

## Operating Systems

### Custom Router OS

Purpose:

Primary operating system.

Features:

- Consumer-focused interface
- AI-assisted diagnostics (future)
- Automatic updates
- Premium feature set

---

### OpenWrt

Purpose:

Advanced user operating system.

Features:

- Standard OpenWrt compatibility
- Package management
- Advanced networking
- Development platform

---

# 5. Boot Architecture

Three-position hardware switch:

- Custom OS
- Automatic
- OpenWrt

Boot selection shall occur before operating system execution.

Each operating system shall boot only from its corresponding SPI NOR and NAND storage.

---

# 6. Recovery

Each operating system shall be capable of:

- Verifying firmware
- Flashing the alternate operating system
- Restoring corrupted firmware
- Verifying flash integrity

Recovery shall not require TFTP by default.

---

# 7. Networking

## Wireless

Tri-band Wi-Fi 7

Bands:

- 2.4 GHz
- 5 GHz
- 6 GHz

Four external high-gain antennas.

The product shall support all mandatory and chipset-supported optional Wi-Fi 7 features available on the selected hardware.

---

## Ethernet

Ports:

- 4 × 5 Gbps RJ45 LAN
- 2 × 10 Gbps SFP+ configurable as WAN/LAN

---

## USB

- 2 × USB4 Type-C

Supported use cases:

- External storage
- USB Ethernet
- Cellular modems (where supported)
- Diagnostics
- Recovery
- Future expansion

---

# 8. Security

Hardware secure boot.

Firmware signature verification.

Anti-rollback protection.

Secure element for:

- Device identity
- Certificates
- Cryptographic keys

---

# 9. Cooling System

## Objectives

Maintain safe operating temperatures during sustained full-load operation without excessive noise.

---

## Airflow

Bottom intake.

Removable dust filter.

PWM-controlled fan.

Side exhaust.

---

## Thermal Interface

PTM7950 phase-change thermal interface material shall be used on primary heat-generating integrated circuits where mechanically appropriate.

---

## Cooling Assemblies

Primary assembly:

- CPU
- Ethernet switch
- Major networking controllers

Secondary assembly:

- USB4 controllers
- PMICs
- Additional components requiring thermal assistance

Final allocation shall be validated by thermal simulation.

---

# 10. Chassis

Material:

Premium engineering plastic (PC or PC/ABS blend).

Requirements:

- RF transparent
- High rigidity
- Serviceable
- Attractive appearance

---

# 11. Display

Front OLED display.

Functions:

- Boot progress
- Operating system
- Internet status
- CPU utilization
- Temperature
- Firmware updates
- Recovery progress
- Diagnostic information

---

# 12. RGB Power Indicator

Integrated into the power button.

Functions:

- Power indication
- Boot status
- Firmware updates
- Recovery
- Error diagnostics

Error codes shall be documented on the manufacturer's support website.

---

# 13. Serviceability

Replaceable:

- Fan
- Dust filter
- External power adapter

Accessible service points shall be provided for maintenance and manufacturing diagnostics.

---

# 14. Diagnostics

Built-in hardware diagnostics shall test:

- CPU
- Memory
- NAND
- SPI NOR
- Ethernet
- SFP+
- USB4
- Wi-Fi
- Fan
- Temperature sensors

Results shall be available through both the OLED display and the web interface.

---

# 15. Software Requirements

Custom Router OS shall provide:

- Web interface
- Mobile application support
- Secure updates
- VPN
- QoS
- VLAN
- Multi-WAN
- Firewall
- Guest networks
- Diagnostics
- Firmware rollback

OpenWrt shall remain independently updateable.

---

# 16. Reliability Targets

Expected software support:

10 years.

Target continuous operation:

24 × 7.

Target operating environment:

Residential indoor use.

Firmware updates shall support rollback.

Failure of one operating system shall not prevent operation of the second operating system.

---

# 17. Manufacturing Requirements

- Automated production testing
- Flash programming fixtures
- Functional networking validation
- Wi-Fi RF calibration
- Thermal validation
- Burn-in testing
- Secure key provisioning
- Final firmware verification

---

# 18. Compliance Targets

The final product shall be designed with certification in mind for applicable regions, including:

- Electrical safety
- EMC/EMI
- Radio compliance
- Environmental requirements

Specific certifications will depend on the markets in which the product is sold.

---

# 19. Future Expansion

The architecture should allow future software additions such as:

- New VPN protocols
- Enhanced parental controls
- Cloud management
- Additional diagnostics
- Expanded USB functionality
- Mesh networking enhancements
- Security feature updates

without requiring hardware redesign.

---

# 20. Success Criteria

The product shall:

- Deliver sustained multi-gigabit routing performance without thermal throttling under intended operating conditions.
- Maintain stable operation during continuous 24×7 use.
- Recover from firmware corruption using the independent operating system.
- Support long-term firmware evolution throughout the planned support lifecycle.
- Provide a premium user experience through intuitive software, effective diagnostics, and quiet operation.
