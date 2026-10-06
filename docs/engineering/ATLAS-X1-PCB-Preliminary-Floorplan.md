# ATLAS X1 Preliminary PCB Floorplan

## Objective

Establish a placement strategy before schematic/PCB capture.

## Board orientation

                 REAR / CONNECTOR EDGE
+------------------------------------------------------+
| SFP+  SFP+ | 5G RJ45 x4 | USB4-A | USB4-B | DC IN  |
+------------------------------------------------------+
| Ethernet switch / SerDes       | USB4 controller   |
| PHYs + magnetics               | Type-C PD         |
|                                |                   |
|             +------------------+                   |
|             |                  |                   |
|             |       SoC        |      DDR          |
|             |                  |                   |
|             +------------------+                   |
|                                                    |
| RF keepout / Wi-Fi 7 radio                         |
|        RF front end / antenna feed region           |
|                                                    |
| Storage / security        OLED / control           |
+------------------------------------------------------+
                  FRONT / DISPLAY

## Placement rules

### SoC + DDR
Keep DDR immediately adjacent to the SoC. Follow the selected vendor topology exactly.

### Ethernet
Keep PHYs close to the switch/SerDes. Keep magnetics close to the RJ45 connector boundary.

### SFP+
Keep cages at the connector edge and minimize SerDes path length.

### USB4
Place USB4 controller close to Type-C connectors. Reserve retimer footprints only if channel analysis indicates they are required.

### RF
Keep switching power and Ethernet magnetics away from the RF zone. Preserve vendor-recommended RF keepouts.

### Power
Place high-current switching regulators away from RF and high-speed analog interfaces. Keep their hot loops compact.

## Fan and heatsink

Reserve a central airflow corridor from bottom intake to side exhaust. The primary heatsink must not block RF or connector access.

## Antennas

Four external antenna connectors should be distributed to minimize coupling and maintain the selected radio vendor's MIMO requirements.

## PCB release gate

Do not start final routing until:
- SoC selected;
- DDR selected;
- Ethernet architecture selected;
- USB4 controller selected;
- stack-up approved;
- mechanical envelope approved.
