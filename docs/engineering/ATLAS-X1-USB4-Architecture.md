# ATLAS X1 USB4 Architecture

## 1. Requirement

Provide 2 x USB4 Type-C expansion ports.

Intended uses include:

- external SSD
- USB Ethernet
- cellular modem
- diagnostic equipment
- recovery media
- future expansion

## 2. Architecture

Each port shall be treated as a high-speed subsystem with:

- USB4-capable host/controller path
- Type-C port controller
- CC/PD management
- high-speed ESD protection
- retimer/redriver only if required by channel budget
- controlled-impedance differential routing
- dedicated power protection

## 3. PCIe interaction

The system design shall reserve sufficient PCIe bandwidth for USB4 controllers without starving Wi-Fi, storage or Ethernet.

Lane allocation must be frozen only after the SoC and USB4 controller are selected.

## 4. PCB requirements

- minimize discontinuities;
- use validated via structures;
- use controlled-impedance differential routing;
- avoid unnecessary stubs;
- follow controller vendor channel-loss budget.

## 5. Port protection

Each port requires review of:

- VBUS OCP
- ESD
- CC protection
- over-voltage
- connector thermal rating
- PD policy
- EMI shielding

## 6. Validation

Test with certified USB4 cables and representative SSDs, Ethernet adapters and modems. Verify link negotiation, sustained transfer, hot-plug, suspend/resume, thermal behavior and fault recovery.
