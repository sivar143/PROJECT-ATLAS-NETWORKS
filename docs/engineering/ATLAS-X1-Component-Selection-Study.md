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

## 3. USB4 — ASMedia ASM4242

ASM4242 remains a strong candidate because it provides PCIe Gen4 x4 for two USB 40Gbps ports.

Blocking dependencies:
- host must expose Gen4 x4;
- Linux/OpenWrt driver support must be demonstrated;
- channel loss must be simulated;
- Type-C/PD architecture must be validated.

Status: **Candidate — not selected.**

## 4. 5GbE copper PHY

Marvell's Alaska M portfolio provides suitable multi-gig PHY families. The preferred direction is a quad-port 5G/2.5G/1G PHY or quad-port 10G/5G/2.5G/1G PHY, subject to host interface compatibility and availability.

Status: **Candidate family — not selected.**

## 5. USB Type-C PD

TI TPS26750/TPS26750A are candidate PD controllers. TPS26750A is an active PD 3.2 controller supporting source/sink/DRP and EPR.

The product will not advertise the controller's maximum theoretical PD power automatically. The actual port power will be limited by the system power and thermal budget.

Status: **Candidate — not selected.**

## 6. Secure element

Microchip ATECC608 TrustFLEX-family devices are candidates for device identity and private-key protection.

Status: **Candidate — not selected.**

## 7. Required architecture change

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

## 8. Selection gate

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
