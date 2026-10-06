# ATLAS X1 Engineering Design Decisions

## DDR-001 — Preserve 8 GB memory requirement

Decision: retain 8 GB as the architecture target.

Reason: the product combines routing, Wi-Fi management, diagnostics, VPN, security services, local history and a dual-OS concept. Final memory technology remains dependent on SoC compatibility.

## DDR-002 — Keep dual independent OS storage domains

Decision: retain separate SPI NOR + NAND domains for AtlasOS and OpenWrt.

Reason: the product requirement explicitly prioritizes fault isolation and independent recovery.

## DDR-003 — USB4 controller direction

Decision: prefer a controller architecture capable of exposing both USB4 ports from one PCIe Gen4 x4 interface.

Candidate: ASMedia ASM4242.

Status: candidate only.

## DDR-004 — IPQ9574 is not the final SoC

Decision: do not select IPQ9574 for the current X1 PDS.

Reason: upstream Linux documentation identifies its PCIe controllers as Gen3 x1/x2, while the PDS requires PCIe Gen4.

IPQ9574 remains a fallback only if the PDS is formally revised.

## DDR-005 — Filogic 880 is not the final SoC

Decision: do not select Filogic 880 for the current X1 PDS.

Reason: MediaTek documents PCIe 3.0 and a native Ethernet mix that does not directly match the X1 port budget.

## DDR-006 — Treat the four 5GbE + two 10GbE requirement as a system-level networking budget

Decision: do not assume all six ports are native SoC MACs.

Reason: the final implementation may use an external multi-gig switch/fabric and PHYs.

## DDR-007 — PCIe Gen4 remains a hard PDS requirement

Decision: retain PCIe Gen4 until the project owner formally approves a PDS change.

Reason: the two-port USB4 architecture benefits from a Gen4 x4 host connection, and silently reducing the requirement would invalidate the existing PDS.

## DDR-008 — Thermal design remains active

Decision: retain replaceable filtered forced-air cooling in the baseline.

Reason: sustained multi-gig networking, Wi-Fi 7, USB4 and multiple high-speed PHYs create a significant thermal load.

## DDR-009 — No fabrication release from architecture documents

Decision: schematic/PCB release requires component selection, reference-design review, SI/PI, thermal and mechanical validation.

## DDR-010 — Architecture B is an approved fallback path for investigation

Decision: if no integrated ARM networking SoC meets the full PDS, investigate a split architecture consisting of:
- ARM network/application processor;
- dedicated Wi-Fi 7 platform;
- external Ethernet switch/fabric;
- PCIe Gen4 USB4 controller.

This is an investigation path, not a final architecture.
