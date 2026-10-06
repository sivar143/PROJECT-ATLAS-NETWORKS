# ATLAS X1 Thermal and Airflow Design

## Status

Preliminary thermal engineering baseline.

## 1. Cooling architecture

The PDS requires:
- bottom filtered intake;
- PWM-controlled fan;
- primary heat removal for CPU/networking/high-speed silicon;
- secondary cooling for USB4/PMIC hot spots;
- side exhaust;
- PTM7950 phase-change material where mechanically appropriate.

## 2. Airflow path

BOTTOM FILTER -> FAN -> PRIMARY HEATSINK -> SECONDARY ZONE -> LEFT/RIGHT EXHAUST

The fan shroud shall minimize bypass flow around the primary heatsink.

## 3. Thermal hierarchy

Priority 1:
- networking/ARM SoC;
- Ethernet switch/fabric;
- high-power Wi-Fi components.

Priority 2:
- 5GbE PHYs;
- USB4 controller;
- PCIe/retimer if populated;
- major PMICs.

Priority 3:
- DDR;
- storage;
- security;
- auxiliary controllers.

## 4. Heatsink concept

Use a common primary heat spreader only when component height and electrical isolation permit.

The primary assembly shall have:
- adequate fin area;
- low thermal resistance;
- controlled fan airflow;
- no obstruction to RF feeds;
- serviceable attachment;
- PTM7950 on appropriate high-dissipation ICs.

Do not bridge unrelated IC packages with a heatsink unless mechanical and electrical isolation is verified.

## 5. Secondary thermal assembly

Use smaller heatsinks or a secondary heat spreader for USB4, PMIC and PHY hot spots that exceed the validated temperature budget.

Thermal pads shall be selected for compression, conductivity and long-term reliability.

## 6. Fan

The fan shall provide:
- PWM control;
- tachometer feedback;
- stall detection;
- startup verification;
- closed-loop temperature control;
- fault telemetry.

Fan selection shall be based on acoustic performance at required static pressure, not free-air CFM alone.

## 7. Filter

The filter shall be:
- removable;
- washable or replaceable as selected;
- accessible without PCB removal;
- sized so pressure drop remains acceptable at end-of-life loading.

Filter pressure drop shall be included in CFD and fan operating-point calculations.

## 8. Thermal sensors

At minimum monitor:
- SoC;
- Ethernet switch/fabric;
- RF module;
- USB4 controller;
- inlet air;
- exhaust air;
- PCB hotspot(s).

Firmware shall correlate temperature with fan speed and workload.

## 9. Thermal protection

Hardware protection shall remain active even if firmware fails where practical.

Implement:
- hardware over-temperature protection in ICs;
- regulator thermal shutdown;
- fan fault detection;
- controlled workload reduction;
- emergency power reduction/shutdown if validated limits are exceeded.

## 10. CFD/thermal simulation

Include:
- component heat map;
- airflow velocity;
- pressure drop;
- heatsink temperature;
- PCB temperature;
- inlet/exhaust temperature;
- filter loading cases.

Cases:
1. idle;
2. normal routing;
3. Wi-Fi sustained;
4. Ethernet sustained;
5. USB4 sustained;
6. maximum simultaneous load;
7. high ambient;
8. partially loaded filter.

## 11. Acoustic target

Do not freeze a single dBA value before fan/heatsink/air-path testing.

Target quiet continuous operation under typical residential load, with controlled fan escalation under sustained worst-case load.

## 12. Thermal release gate

Require measured EVT correlation between:
- thermal model;
- fan operating point;
- component junction temperature;
- enclosure surface temperature;
- acoustic output;
- worst-case workload.
