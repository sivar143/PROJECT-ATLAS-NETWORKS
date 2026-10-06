# ATLAS X1 RF and Networking Architecture

## 1. Wi-Fi 7

Required bands:

- 2.4 GHz
- 5 GHz
- 6 GHz

Target features, subject to chipset capability and regulatory approval:

- MLO
- 4096-QAM
- OFDMA
- MU-MIMO
- beamforming
- Multi-RU
- preamble puncturing
- 320 MHz channels
- WPA3

## 2. RF partition

The PCB shall reserve a clean RF zone with controlled impedance routing and clear separation from:

- switching regulators
- high-current USB power paths
- fan motor circuitry
- noisy clocks
- Ethernet magnetics/SerDes where practical

The four external antenna interfaces must have matched, length-controlled RF paths.

## 3. Antenna architecture

Four external high-gain antennas are required by the PDS. The final radio chain count, FEM/LNA/PA topology and antenna mapping depend on the selected Wi-Fi 7 chipset.

Antenna diversity/MIMO mapping shall be validated with the selected radio reference design.

## 4. Ethernet

Required user-facing connectivity:

- 4 x 5 Gbps RJ45 LAN
- 2 x 10 Gbps SFP+ configurable WAN/LAN

The Ethernet architecture must define whether 5GbE is provided by the main SoC, an external switch, or a combination.

## 5. SFP+

Each SFP+ cage requires:

- SerDes lane
- module detect
- I2C management
- TX disable
- LOS/fault handling where required
- ESD/EMI treatment
- thermal clearance

The final SFP+ implementation shall be validated against the selected switch/PHY reference design.

## 6. VLAN and routing

Hardware/software shall support:

- tagged and untagged VLANs
- multiple routed subnets
- guest isolation
- IoT isolation
- multi-WAN
- QoS
- IPv4/IPv6 firewalling
- policy-based routing where supported

## 7. RF validation

EVT/DVT shall include conducted and OTA measurements, sensitivity, throughput, MLO behavior, coexistence, thermal derating, antenna matching and regulatory pre-scan.
