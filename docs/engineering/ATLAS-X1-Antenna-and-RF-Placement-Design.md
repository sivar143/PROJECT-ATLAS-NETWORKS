# ATLAS X1 Antenna and RF Placement Design

## Status

Preliminary RF/mechanical placement baseline. Final RF geometry remains dependent on the selected Wi-Fi 7 platform and vendor reference design.

## 1. RF objective

Provide tri-band 2.4 GHz / 5 GHz / 6 GHz Wi-Fi 7 coverage while preserving MIMO isolation, antenna efficiency, regulatory margin and coexistence with high-speed digital electronics.

## 2. Four-antenna mechanical baseline

The PDS requires four external high-gain antennas.

Preliminary arrangement:

                 REAR
        A ================= B
        |                    |
        |      PCB / RF      |
        |                    |
        C ================= D
                 FRONT

A/B are rear-corner antennas. C/D are front/side-corner antennas.

The four antennas shall be physically separated as much as the enclosure allows. Final spacing shall be validated against the selected antenna radiation pattern and radio reference design.

## 3. Polarization strategy

Do not place all four antennas in the same physical orientation.

Initial mechanical target:
- A: vertical;
- B: vertical;
- C: approximately +45 degrees;
- D: approximately -45 degrees.

This is a starting geometry only. Final orientation shall be selected from measured S-parameters and OTA testing.

## 4. Antenna type

Preferred baseline:
- external articulated dipole or equivalent broadband tri-band antenna;
- 2.4/5/6 GHz coverage;
- matched to the selected radio;
- production-qualified with measured radiation pattern;
- connectorized for service replacement.

The four physical antennas do not by themselves define the final spatial-stream count. The selected Wi-Fi platform determines the chain allocation.

## 5. RF feed architecture

Radio RF port -> matching/filter/FEM -> RF protection as required -> controlled-impedance coax -> board connector -> external antenna

Do not place ordinary current-sense resistors in RF signal paths.

RF safety/monitoring shall use appropriate RF power, temperature and mismatch/VSWR telemetry where supported, with transmit-power reduction on abnormal conditions.

## 6. PCB RF zone

Reserve one continuous RF region along an enclosure edge.

Rules:
- no switching-regulator hot loops in RF zone;
- no Ethernet magnetics in RF zone;
- no fan motor directly adjacent to RF feedlines;
- no high-speed digital clock routing through antenna feed corridors;
- continuous controlled RF reference plane;
- via fencing where the vendor reference design permits;
- preserve vendor RF keepouts.

## 7. Antenna clearance

The antenna manufacturer's keepout is authoritative.

Maintain clear space around radiating structures and keep digital copper/components away from the antenna element. For external antennas, maintain clearance from heatsinks, SFP cages, RJ45 magnetics, USB-C shells, fan motor and DC wiring.

## 8. RF/digital partition

Recommended top view:

[ANT A]   [RF/FEM/RADIO]   [ANT B]
-----------------------------------
[ RF keepout / feed region ]
-----------------------------------
[ SoC + DDR ] [ USB4 ] [ Ethernet ]
-----------------------------------
[                 POWER          ]

The RF region shall be physically separated from major switching and high-current zones.

## 9. Coax routing

Use short controlled-impedance 50-ohm paths.

Requirements:
- avoid sharp bends;
- avoid unnecessary vias;
- maintain continuous ground reference;
- use qualified board-to-coax connectors;
- secure coax mechanically;
- prevent coax from moving parts;
- validate insertion and return loss.

## 10. Wi-Fi 7 stream mapping

The final mapping shall be generated only after the selected radio platform is frozen.

Document:
- 2.4 GHz chains;
- 5 GHz chains;
- 6 GHz chains;
- MLO grouping;
- FEM allocation;
- antenna polarization;
- antenna isolation;
- measured S-parameters;
- conducted output power;
- OTA TRP/TIS;
- regulatory power limits.

## 11. RF coexistence

Treat DDR, PCIe, USB4, Ethernet SerDes, switching regulators, fan PWM, OLED and high-speed clocks as RF noise sources.

Review clock harmonics and DC/DC switching frequencies against Wi-Fi operating bands.

## 12. RF verification gate

Before antenna freeze:
- vendor reference layout reviewed;
- antenna datasheet and mechanical drawing approved;
- enclosure RF material characterized;
- antenna S-parameters measured;
- isolation measured;
- conducted sensitivity testing completed;
- OTA chamber testing completed;
- coexistence testing completed;
- regulatory pre-scan completed.
