# ATLAS X1 Latest-Generation Silicon Policy

## Purpose

ATLAS X1 shall use the newest **production-qualified, commercially orderable** silicon that meets the required interface, performance, efficiency, thermal and Linux/OpenWrt requirements.

"Latest" does not mean selecting a preview, announcement-only, evaluation-only or unreleased device. A newer device is eligible only after production status, documentation, supply, software support and electrical characteristics are verified.

## 1. USB controller policy — highest priority

The previous ASM4242 direction is **withdrawn as a final selection**.

ASM4242 is a first-generation USB4 host controller supporting USB4 Gen3x2 up to 40Gbps and PCIe Gen4 x4. It remains useful only as a fallback/reference device. citeturn1search6turn1search7

The X1 engineering target is now:

- USB4 Version 2.0 / USB4 Gen4;
- up to 80Gbps symmetric operation;
- support for the 120/40Gbps asymmetric mode where appropriate;
- PCIe tunnelling;
- USB 3.x backward compatibility;
- DisplayPort tunnelling/Alt Mode where required;
- Linux/OpenWrt support;
- production-qualified silicon.

USB-IF's current specification supports 80Gbps operation, and the USB4 v2 specification and Gen4 compliance material are now published. citeturn1search0turn1search1

ASMedia has publicly demonstrated 12nm USB4 80Gbps PHY technology with PCIe Gen5 upstream capability, but this is not being treated as a production controller selection until an orderable controller part and complete design documentation are available. citeturn1search4

**Selection rule:** do not freeze ASM4242 or another 40Gbps-only host controller into the production schematic.

## 2. Ethernet silicon policy

For the four RJ45 ports, prioritize the newest low-power multi-gig PHYs with:

- 5GbE minimum;
- 2.5/1/100Mb/s fallback;
- IEEE 802.3az Energy Efficient Ethernet;
- low active and idle power;
- 100m Cat5e/Cat6 operation;
- thermal-efficient package;
- Linux driver/reference-design support;
- long-term availability.

The current preferred candidate family is **Marvell Alaska M**, with the exact production part selected after host-interface and power measurements. The family includes current quad-port 5G and 10G/5G/2.5G PHYs and explicitly targets low power and Wi-Fi 7 infrastructure. citeturn1search10

For the two SFP+ ports, prefer direct high-speed SerDes/SFI connectivity from the Ethernet fabric rather than adding unnecessary copper PHY silicon.

## 3. Ethernet controller/switch policy

Do not add an external Ethernet switch merely because it is newer.

The selected fabric must minimize:
- total active power;
- idle power;
- SerDes count;
- conversion stages;
- thermal hotspots;
- PCB routing complexity.

Current Broadcom Wi-Fi 8 switch silicon demonstrates the newest generation of highly integrated multi-gig networking architecture, but its enterprise port density is far beyond the X1 requirement. It is therefore a technology reference, not an automatic X1 selection. citeturn0search8

## 4. Power silicon policy

Power conversion shall use the newest production-qualified high-efficiency regulators that are appropriately sized for each rail.

A current high-priority candidate for high-current X1 rails is **TI TPS544B28**:
- 20A continuous;
- synchronous buck;
- PMBus 1.4;
- integrated MOSFETs;
- differential remote sense;
- selectable Eco-mode/FCCM;
- current telemetry;
- released as an active device in 2026. citeturn2search2

For rails requiring substantially higher current, the design may use a current 40A-class production regulator such as TI TPS548D26, subject to efficiency and thermal comparison. citeturn2search1

Newer preview-only silicon such as TPS544E27 shall **not** be frozen into the production BOM until TI changes it to production status and full qualification/supply evidence is available. citeturn2search0

## 5. USB-C PD policy

USB-C PD controllers shall be selected from the newest production-qualified PD generation and must support the latest applicable USB Type-C/PD specification.

Power capability will be limited by the X1 system power budget. A controller's theoretical maximum PD capability must never be interpreted as the product's advertised port power.

## 6. General silicon selection gate

A component is not considered "latest and efficient" merely because it has a newer announcement date.

Before schematic freeze, every major IC shall pass:

1. Production status verification.
2. Datasheet/revision verification.
3. Power-efficiency comparison against the previous candidate.
4. Thermal-loss calculation.
5. Linux/OpenWrt support review.
6. Reference-design availability review.
7. Supply/lifecycle review.
8. SI/PI impact review.
9. Security review.
10. Worst-case simultaneous-load validation.

## Current decision

**USB:** move the production target from USB4 40Gbps to USB4 Version 2 / 80Gbps. ASM4242 is fallback/reference only.

**Ethernet:** use the newest production-qualified low-power multi-gig PHY/fabric available at schematic freeze; Marvell Alaska M remains a leading candidate.

**Power:** use current production high-efficiency digital/synchronous regulators sized per rail; TI TPS544B28 is a leading high-current candidate, with 40A-class alternatives evaluated where necessary.

No final IC is frozen until these gates are completed.
