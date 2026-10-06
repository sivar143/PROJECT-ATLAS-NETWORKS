# ATLAS X1 Engineering Design Decisions

## DDR-001 — Preserve 8 GB memory requirement

Decision: retain 8 GB as the architecture target.

Reason: the product combines routing, Wi-Fi management, diagnostics, VPN, security services, local history and a dual-OS concept. Final memory technology remains dependent on SoC compatibility.

## DDR-002 — Keep dual independent OS storage domains

Decision: retain separate SPI NOR + NAND domains for AtlasOS and OpenWrt.

Reason: the product requirement explicitly prioritizes fault isolation and independent recovery.

## DDR-003 — Use one USB4 host controller for two ports if validated

Decision: prefer a controller architecture capable of exposing both USB4 ports from a single PCIe expansion interface.

Candidate: ASMedia ASM4242.

Reason: this can reduce PCIe resource fragmentation compared with two independent host controllers.

Status: candidate only; driver, signal-integrity, power and commercial validation required.

## DDR-004 — Do not freeze the SoC yet

Decision: keep Qualcomm and MediaTek Wi-Fi 7 platforms as candidates.

Reason: neither published platform specification, by itself, proves that the full X1 interface budget can be satisfied without companion silicon.

## DDR-005 — Treat the four 5GbE + two 10GbE requirement as a system-level networking budget

Decision: do not assume all six ports are native SoC MACs.

Reason: the final implementation may use an external multi-gig switch/PHY and/or SerDes conversion.

## DDR-006 — Keep PCIe Gen4 as an architecture requirement

Decision: retain the PDS PCIe Gen4 requirement until the USB4 implementation and expansion bandwidth are finalized.

Reason: the selected USB4 architecture benefits from a PCIe Gen4 x4-class host link.

## DDR-007 — Thermal design remains active

Decision: keep replaceable filtered forced-air cooling in the baseline.

Reason: sustained multi-gig networking, Wi-Fi 7, USB4 and multiple high-speed PHYs create a significant thermal load. Passive cooling should not be assumed before measured power data exists.

## DDR-008 — No fabrication release from architecture documents

Decision: schematic/PCB release requires component selection, reference-design review, SI/PI, thermal and mechanical validation.

Reason: high-speed buses such as DDR, PCIe, USB4, Ethernet SerDes and Wi-Fi RF cannot be safely finalized from generic rules alone.
