# ATLAS X1 Component Selection Study

## Status

Candidate study only. No component in this document is a released BOM item.

## Critical finding

The initial study treated IPQ9574 as potentially suitable for the PDS PCIe Gen4 requirement. That assumption is now corrected.

Qualcomm's current NPro 7 documentation confirms IPQ9574 as a strong Wi-Fi 7/networking platform, but upstream Linux support documents its PCIe controllers as Gen3 x1/x2. Therefore IPQ9574 does **not** satisfy the PDS PCIe Gen4 requirement.

MediaTek Filogic 880 is also documented with PCIe 3.0 and therefore does not satisfy the current PDS Gen4 requirement.

The project shall not proceed to final SoC selection until this conflict is resolved.

## 1. Candidate A — Qualcomm Dragonwing NPro 7 / IPQ9574

Strengths:
- quad-core ARM Cortex-A73;
- Wi-Fi 7;
- tri-band 2.4/5/6 GHz;
- 10GbE-class networking;
- DDR4 support;
- mature Linux/OpenWrt ecosystem.

Blocking issue:
- PCIe implementation is Gen3, not Gen4.

Decision: **REJECTED against current PDS.**

Fallback status: retain only if the PDS is formally changed from PCIe Gen4 to PCIe Gen3.

## 2. Candidate B — MediaTek Filogic 880

Strengths:
- quad-core Cortex-A73;
- Wi-Fi 7;
- two 10Gbps USXGMII interfaces;
- DDR4;
- strong NPU/network offload;
- SPI-NOR/SPI-NAND support;
- established Linux/OpenWrt ecosystem.

Blocking issues:
- PCIe 3.0;
- native Ethernet mix does not directly provide four 5GbE + two 10GbE SFP+.

Decision: **REJECTED against current PDS.**

Fallback status: useful reference platform for the Wi-Fi/networking architecture.

## 3. USB4 — latest-generation target

The production target is now **USB4 Version 2 / Gen4 up to 80Gbps**, not first-generation 40Gbps USB4.

ASMedia ASM4242 is retained only as a fallback/reference because its published capability is USB4 Gen3x2 up to 40Gbps, despite its PCIe Gen4 x4 upstream interface. citeturn1search6turn1search7

USB-IF now publishes USB4 v2 and Gen4 compliance material, including 80Gbps operation. citeturn1search0turn1search1

Status: **Production controller selection BLOCKED pending an orderable USB4 v2/80Gbps host controller with complete documentation and Linux support.**

## 4. Ethernet — latest-generation low-power PHY

The preferred production direction remains the current Marvell Alaska M multi-gig PHY family, selected by exact port density and host interface after power measurements. The family provides quad-port 5G and quad-port 10G/5G/2.5G options, EEE and other efficiency/security features. citeturn1search10

For the two SFP+ ports, prefer direct SerDes/SFI from the Ethernet fabric where possible to avoid unnecessary PHY power.

Status: **Leading candidate family — exact production part not frozen.**

## 5. USB Type-C PD

USB-C PD will use the newest production-qualified PD controller that satisfies the latest applicable Type-C/PD specification and the X1 source/sink requirements. The product's actual VBUS power limit will be set by the system power and thermal budget.

Status: **Latest-generation production controller selection pending final USB4 architecture.**

The product will not advertise the controller's maximum theoretical PD power automatically. The actual port power will be limited by the system power and thermal budget.

Status: **Candidate — not selected.**

## 6. Power conversion

Power silicon is now subject to a strict newest-production-qualified and efficiency-first rule. TI TPS544B28 is a current 20A synchronous buck candidate with PMBus, integrated MOSFETs, telemetry and Eco-mode/FCCM; it is a strong candidate for high-current X1 rails. citeturn2search2

For rails above its practical operating point, current 40A-class devices such as TPS548D26 may be evaluated. citeturn2search1

Preview-only devices are excluded from the production BOM until they reach production status.

Status: **Leading power candidates identified — final rail-by-rail selection pending SoC and measured load requirements.**

## 7. Secure element

Microchip ATECC608 TrustFLEX-family devices are candidates for device identity and private-key protection.

Status: **Candidate — not selected.**

## 8. Required architecture change

The current PDS requires:

- quad-core ARM;
- Wi-Fi 7;
- PCIe Gen4;
- 4 × 5GbE;
- 2 × 10GbE SFP+;
- 2 × USB4.

The next candidate search must therefore consider either:

### Architecture A — integrated networking SoC
A single ARM networking platform with Gen4 PCIe and sufficient Ethernet fabric.

### Architecture B — split networking platform
A high-performance ARM application/network processor with Gen4 PCIe plus a dedicated Wi-Fi 7 platform and dedicated Ethernet switch/fabric.

Architecture B is currently the more credible fallback if no suitable integrated consumer networking SoC is found.

## 9. Selection gate

No schematic pinout is frozen until a candidate passes:
- PCIe generation/lane test;
- Ethernet lane budget;
- DDR topology;
- storage interface budget;
- secure-boot review;
- Linux/OpenWrt support;
- thermal budget;
- power budget;
- lifecycle review;
- preliminary SI/PI review.
