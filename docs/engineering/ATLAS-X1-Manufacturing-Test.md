# ATLAS X1 Manufacturing and Production Test

## 1. Manufacturing flow

PCB assembly
   |
AOI / X-ray as applicable
   |
Power-on safety test
   |
Secure provisioning
   |
Flash programming
   |
Boot self-test
   |
Memory/storage test
   |
Ethernet test
   |
SFP+ test
   |
USB4 test
   |
Wi-Fi/RF calibration
   |
Thermal/fan test
   |
Burn-in
   |
Final firmware/configuration
   |
Serial-number traceability
   |
Final inspection

## 2. Board-level tests

At minimum verify:

- input current
- major rail voltages
- power-good sequence
- reset behavior
- DDR
- SPI NOR A/B
- NAND A/B
- secure element
- SoC
- Ethernet
- SFP+
- USB4
- Wi-Fi
- fan/tach
- OLED
- RGB button

## 3. Networking tests

Automated fixture testing shall verify:

- each RJ45 port
- 5GbE negotiation
- SFP+ module detection
- VLAN loopback
- throughput
- packet loss
- link recovery
- WAN/LAN role switching

## 4. Wireless tests

The production process shall distinguish factory RF calibration from regulatory certification. Required checks include:

- radio bring-up
- calibration data integrity
- transmit/receive sanity
- antenna path validation
- temperature telemetry

Full RF performance validation remains a DVT/certification activity.

## 5. Secure provisioning

The factory station must record:

- serial number
- MAC addresses
- secure-element identity/certificate result
- firmware version
- hardware revision
- test result
- timestamp
- fixture/station ID

Sensitive private key material must not be exported from protected hardware where the selected security architecture permits.

## 6. Traceability

Every production unit shall be traceable to:

- PCB revision
- BOM revision
- firmware release
- manufacturing lot
- test station
- calibration record
