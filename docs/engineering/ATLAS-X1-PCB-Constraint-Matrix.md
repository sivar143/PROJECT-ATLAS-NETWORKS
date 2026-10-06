# ATLAS X1 PCB Constraint Matrix

## Purpose

Provide a single preliminary constraint set for schematic/PCB capture. Values marked "vendor" shall be replaced by the selected component's official layout guide before routing.

## 1. Global

| Net class | Preliminary rule | Freeze authority |
|---|---|---|
| RF | 50 ohm controlled impedance | RF vendor + fabricator |
| PCIe Gen4 | Differential, vendor impedance | SoC/USB4 vendor |
| USB4 | Differential, vendor impedance | USB4 controller vendor |
| Ethernet SerDes | Vendor-specific differential impedance | PHY/switch vendor |
| DDR | Vendor topology/impedance | SoC/memory vendor |
| Clocks | Short, controlled return path | SoC vendor |
| Power | Low-inductance planes/traces | PI analysis |

## 2. Placement priority

1. SoC + DDR.
2. PCIe Gen4 / USB4.
3. Ethernet switch/fabric and SerDes.
4. Wi-Fi RF/FEM.
5. Power conversion.
6. Storage/security.
7. control/display/test.

Placement shall be re-ordered where a selected vendor reference design explicitly requires another topology.

## 3. DDR

- Follow exact vendor topology.
- Minimize layer transitions.
- Maintain continuous reference.
- Keep unrelated high-speed clocks out of the DDR escape region.
- Validate length matching using vendor constraints rather than generic values.

## 4. PCIe Gen4

- Preserve PCIe Gen4 as a hard PDS requirement.
- Keep the x4 route direct between host and USB4 controller where architecture permits.
- Avoid unnecessary vias.
- Maintain continuous reference planes.
- Perform insertion-loss, return-loss and crosstalk analysis before routing freeze.
- Retimer/redriver only when channel analysis demonstrates need.

## 5. USB4

- Keep controller close to Type-C connectors.
- Minimize discontinuities through connector, ESD and mux structures.
- Select protection devices specifically qualified for USB4 bandwidth.
- Do not insert ordinary current-sense elements into SuperSpeed/USB4 differential pairs.
- VBUS protection/sensing shall be on the power path, not the data path.
- Reserve optional retimer footprints only if the final channel budget requires them.

## 6. Ethernet

- Keep switch/fabric-to-PHY routes short.
- Keep PHY-to-magnetics/RJ45 paths compliant with PHY vendor layout rules.
- Keep SFP SerDes direct to cage/module path.
- Place ESD/transient protection according to PHY/magnetics vendor recommendations.
- No conventional current sensor in differential pairs.

## 7. RF

- Use controlled 50-ohm RF traces.
- Maintain continuous reference.
- Keep RF feedlines away from switching nodes and high-speed clocks.
- Use via fencing where required by the RF reference design.
- Do not route unrelated digital signals through RF keepouts.

## 8. Power integrity

- Minimize regulator hot-loop area.
- Place input/output capacitors according to regulator reference layout.
- Keep high-current paths short and wide.
- Separate noisy switching nodes from RF.
- Each protected branch shall include the ATLAS-required protection and voltage/current sensing.
- Include protection/sensing voltage drop and thermal dissipation in PI analysis.

## 9. Mechanical constraints

PCB CAD shall include:
- enclosure outline;
- mounting holes;
- connector keepouts;
- heatsink keepouts;
- fan keepout;
- antenna connector locations;
- OLED/button keepouts;
- service-access keepouts.

## 10. Release checks

Before routing release:
- stack-up approved;
- impedance calculator results archived;
- selected-vendor constraints imported;
- pin/lane map frozen;
- mechanical coordinates frozen;
- RF keepouts frozen;
- safety/protection placement reviewed.

Before fabrication:
- DRC complete;
- SI/PI complete;
- thermal review complete;
- RF review complete;
- DFM complete;
- manufacturing test access verified.
