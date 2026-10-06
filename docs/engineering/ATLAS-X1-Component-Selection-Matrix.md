# ATLAS X1 Component Selection Matrix

## Selection phase

This document is the working Phase-5 selection matrix for the X1. It supersedes the earlier informal candidate list but does not constitute a released BOM.

## 1. Hard requirements from the PDS

| Function | Requirement | Selection consequence |
|---|---|---|
| CPU | Quad-core 64-bit ARM | Candidate SoC must be ARM64 and quad-core |
| Networking | Hardware acceleration | SoC/platform must provide packet/NAT acceleration |
| Wi-Fi | Tri-band Wi-Fi 7 | Integrated radio or validated companion Wi-Fi 7 platform |
| Wired | 4 × 5GbE RJ45 | Four 5GBASE-T copper paths |
| Wired | 2 × 10GbE SFP+ | Two 10Gb/s SerDes/SFP+ paths |
| USB | 2 × USB4 Type-C | Host controller with validated Linux support |
| Expansion | PCIe Gen4 | Must be preserved unless PDS is formally revised |
| Memory | 8 GB DDR4/LPDDR4X | Must be supported by selected SoC |
| Storage | 2 × independent NOR + NAND domains | Must have sufficient SPI/NAND interfaces |
| Security | Secure boot + secure element | Hardware root of trust |
| Thermal | Forced-air, serviceable | System power must support realistic fan/heatsink design |

## 2. Candidate score

Scoring: 5 = strong fit, 3 = workable with significant companion silicon, 1 = requirement conflict.

| Candidate | ARM quad | Wi-Fi 7 | 10GbE | 5GbE | PCIe Gen4 | DDR4 | Open/Linux path | Overall |
|---|---:|---:|---:|---:|---:|---:|---:|---|
| Qualcomm IPQ9574 | 5 | 5 | 5 | 5 | **1** | 5 | 5 | **Not compliant** |
| MediaTek Filogic 880 | 5 | 5 | 5 | 3 | **1** | 5 | 5 | **Not compliant** |
| New ARM networking platform — TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD | **Preferred search path** |

## 3. Qualcomm IPQ9574

Qualcomm's current NPro 7 page identifies IPQ9574 as a quad-core 2.2 GHz platform with Wi-Fi 7, 6 Ethernet ports and DDR3L/DDR4 support. The upstream Linux device tree documents four PCIe root complexes, with the relevant ports implemented as Gen3 x1/x2 rather than Gen4.

Conclusion: **excellent networking/Wi-Fi candidate, rejected for the current X1 PDS because of the PCIe Gen4 requirement.**

The IPQ9574 should remain a fallback only if the PDS is formally changed to PCIe Gen3.

## 4. MediaTek Filogic 880

MediaTek's current product page identifies a quad-core Cortex-A73 platform with Wi-Fi 7, two 10Gbps USXGMII interfaces, one 2.5GbE PHY plus four 1GbE ports, DDR4 support, PCIe 3.0 and USB 3.0.

Conclusion: **strong Wi-Fi/networking candidate but rejected for the current X1 PDS because the published expansion interface is PCIe 3.0 and the native Ethernet mix does not match the port budget.**

## 5. Required next search

The preferred platform must satisfy the PDS without weakening the USB4 or PCIe requirement.

Search categories:

1. ARM networking SoC with PCIe Gen4.
2. Separate ARM networking CPU + Wi-Fi 7 radio if necessary.
3. Networking processor with 10GbE SerDes and Gen4 PCIe.
4. Long-lifecycle industrial/prosumer silicon with Linux BSP support.

A platform that meets PCIe Gen4 but loses integrated Wi-Fi 7 is acceptable for the next candidate round if the total architecture remains technically and commercially realistic.

## 6. Copper PHY direction

For four 5GbE RJ45 ports, the preferred architecture is a quad-port 5GBASE-T PHY or four single-port PHYs.

Marvell's current Alaska M portfolio includes:
- M 2540 — quad-port 5-speed 10/100/1G/2.5G/5G PHY;
- M 3540 — quad-port 6-speed 10/100/1G/2.5G/5G/10G PHY;
- M 413C — quad-port 6-speed 10/100/1G/2.5G/5G/10G PHY.

The quad-port device is preferred if its host interface and lifecycle are compatible with the selected switch/SoC.

## 7. USB4 direction

The production target is now **USB4 Version 2 / Gen4 up to 80Gbps**. ASM4242 is retained only as a fallback/reference because it is a first-generation 40Gbps USB4 host controller.

The production controller shall not be frozen until an orderable USB4 v2/80Gbps host controller passes:
- PCIe Gen4/Gen5 host-interface validation;
- Linux/OpenWrt driver support;
- USB4 v2 compliance/interoperability review;
- Type-C/PD controller validation;
- channel-loss simulation;
- power/thermal measurement.

A 40Gbps-only controller is not acceptable as the final production choice.

## 8. Type-C/PD direction

Use the newest production-qualified USB PD controller available at schematic freeze. The controller must support the latest applicable USB Type-C/PD requirements, source/sink/DRP as required, robust protection and Linux-host controllability where applicable.

Do not freeze a controller solely because it has a higher theoretical wattage. The actual X1 VBUS power limit shall be derived from the system power and thermal budget.

For X1, the USB-C power policy should initially be **data-host + controlled source/DRP**, not a blanket 240 W port assumption. The actual VBUS power budget must be set by thermal and system power analysis.

## 9. Security direction

Microchip ATECC608-family TrustFLEX parts are candidate secure elements for device identity and certificate/private-key protection.

The secure element is not itself the complete secure-boot root; the selected SoC's secure-boot mechanism and boot ROM must be the primary firmware trust chain.

## 10. Latest-generation silicon gate

All USB, Ethernet and power ICs are now subject to the repository-wide latest-generation silicon policy in `ATLAS-X1-Latest-Generation-Silicon-Policy.md`.

The design must prefer the newest production-qualified, orderable and efficient device that satisfies the interface requirements. Preview/unreleased silicon shall not be frozen into the production BOM.

## 11. Decision

**No final SoC or peripheral silicon set selected yet.**

The previous assumption that IPQ9574 could satisfy the PCIe Gen4 requirement is explicitly withdrawn. This is a required correction before schematic capture.
