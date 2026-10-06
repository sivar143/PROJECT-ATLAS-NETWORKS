# ATLAS X1 Engineering Selection Checklist

## Gate A — Platform

- [ ] ARM64 quad-core SoC selected
- [ ] Wi-Fi 7 architecture selected
- [ ] 8 GB memory topology validated
- [ ] PCIe Gen4 x4 available for USB4
- [ ] secure boot documented
- [ ] Linux/OpenWrt BSP validated
- [ ] lifecycle/availability confirmed

## Gate B — Ethernet

- [ ] switch/fabric selected
- [ ] 4 × 5GbE PHY solution selected
- [ ] 2 × 10GbE SFP+ SerDes selected
- [ ] SFP management path defined
- [ ] magnetics selected
- [ ] ESD devices selected
- [ ] per-port data safety/protection and fault-monitoring architecture defined

## Gate C — USB4

- [ ] USB4 host selected
- [ ] Type-C controller selected
- [ ] PD policy defined
- [ ] ESD selected
- [ ] retimer decision completed
- [ ] Linux/OpenWrt driver validated
- [ ] USB-C/USB4 power protection and sensing defined
- [ ] high-speed protection/sensing reviewed for SI impact

## Gate D — Storage/security

- [ ] NOR A selected
- [ ] NAND A selected
- [ ] NOR B selected
- [ ] NAND B selected
- [ ] secure element selected
- [ ] boot selector architecture frozen
- [ ] manufacturing provisioning flow defined
- [ ] storage power branches protected and sensed

## Gate E — Power/thermal

- [ ] system power budget completed
- [ ] adapter rating derived from measurements
- [ ] regulators selected
- [ ] every separately protected power branch has a fuse/eFuse or equivalent protection
- [ ] every applicable power rail has voltage/current sensing
- [ ] protection trip and fault telemetry defined
- [ ] heatsink envelope defined
- [ ] fan selected
- [ ] filter selected
- [ ] thermal sensors selected
- [ ] protection/sensing losses included in the power budget

## Gate F — PCB

- [ ] stack-up selected
- [ ] impedance targets calculated
- [ ] SI/PI constraints imported
- [ ] mechanical envelope frozen
- [ ] connector datum and mounting-hole coordinates frozen
- [ ] antenna locations and articulation envelope defined
- [ ] RF/digital zoning approved
- [ ] fan/filter/heatsink envelope coordinated with PCB
- [ ] PCB-to-mechanical tolerance stack reviewed
- [ ] schematic ERC strategy defined
- [ ] DFM requirements defined
- [ ] protection devices placed for fault containment
- [ ] high-speed data protection/sensing does not compromise SI/PI

## Gate G — Release

- [ ] schematic review
- [ ] BOM lifecycle review
- [ ] SI/PI review
- [ ] thermal review
- [ ] airflow/CFD review
- [ ] antenna/RF placement review
- [ ] enclosure serviceability review
- [ ] mechanical review
- [ ] security review
- [ ] power/data safety architecture review
- [ ] fault-isolation and recovery test plan approved
- [ ] manufacturing review
- [ ] EVT test plan approved
