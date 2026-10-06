# ATLAS X1 Component Selection Study

## Status

Candidate study only. No component in this document is a released BOM item.

## 1. Networking/Wi-Fi platform candidates

### Candidate A — Qualcomm Dragonwing NPro 7 / IPQ9574 family

Qualcomm documentation identifies IPQ9574 in the NPro 7 family and specifies quad-core Arm CPU, Wi-Fi 7, up to 33 Gbps peak PHY capacity, 6 Ethernet ports with combinations including 2.5GbE, 5GbE and 10GbE, DDR3L/DDR4 support, and PCIe interfaces.

Strengths:
- strong Wi-Fi 7 positioning;
- 10GbE-class networking;
- mature OpenWrt/community interest around Qualcomm networking platforms;
- suitable performance class for X1.

Open items:
- exact PCIe generation/lane allocation must be confirmed from the NDA/reference-design documentation;
- exact Ethernet MAC/SerDes lane map must be confirmed;
- exact radio-chain/FEM architecture must be confirmed;
- USB4 host-controller integration must be validated;
- lifecycle and commercial availability must be confirmed.

### Candidate B — MediaTek Filogic 880 / MT7988 + MT7996 platform

MediaTek documents identify Filogic 880 as a Wi-Fi 7 router/AP platform with quad-core Cortex-A73 CPU, NPU, tri-band 2.4/5/6 GHz operation, 36 Gbps maximum PHY rate, two 10Gbps USXGMII interfaces, one 2.5GbE interface and four 1GbE switch ports. The published platform exposes PCIe 3.0 and USB 3.x rather than USB4.

Strengths:
- strong Wi-Fi 7 feature set;
- explicit OpenWrt support path;
- two native 10GbE interfaces;
- mature reference platforms.

Open items:
- the published interface set does not directly match four 5GbE + two 10GbE SFP+ + two USB4 ports;
- additional switching/PHY/USB4 silicon would be required;
- PCIe 3.0 interface may conflict with the current X1 PCIe Gen4 requirement.

## 2. USB4 candidate

### ASMedia ASM4242

ASM4242 is a USB4 host controller with a PCIe Gen4 x4 upstream interface and two USB4 downstream ports. This makes it architecturally attractive because one controller can service the required two USB4 Type-C ports.

Required validation:
- SoC PCIe lane availability and generation;
- Linux/OpenWrt driver support;
- Type-C/PD controller selection;
- channel-loss and retimer requirements;
- simultaneous USB4 traffic with Wi-Fi/Ethernet loads;
- thermal impact.

## 3. Preliminary direction

The current X1 requirements strongly favor a networking SoC/platform with:

1. Wi-Fi 7 integrated or tightly coupled;
2. at least two 10GbE-class interfaces;
3. multiple multi-gig Ethernet interfaces;
4. PCIe Gen4 x4-class expansion for USB4;
5. DDR4 support;
6. secure boot;
7. Linux/OpenWrt support;
8. long lifecycle.

No candidate is approved until the complete lane map and reference design satisfy the entire X1 interface budget.

## 4. Important architecture finding

The existing PDS combines a very ambitious interface set:

- 4 x 5GbE RJ45;
- 2 x 10GbE SFP+;
- 2 x USB4;
- tri-band Wi-Fi 7;
- dual independent NOR/NAND OS domains.

A single consumer networking SoC is unlikely to expose all of these resources directly. The final board will probably require companion switching/PHY and USB4 silicon.

Therefore the engineering architecture must preserve a flexible high-speed expansion fabric rather than prematurely tying every port directly to the SoC.

## 5. Selection gates

A candidate becomes the selected platform only after:

- NDA/reference documentation review;
- lane-map review;
- power budget;
- thermal budget;
- BSP/OpenWrt validation;
- lifecycle/availability review;
- security review;
- preliminary SI/PI review;
- cost/BOM review;
- regulatory suitability review.

## Sources reviewed

- Qualcomm Dragonwing NPro 7 platform documentation.
- MediaTek Filogic 880 product documentation.
- ASMedia ASM4242 product documentation.
