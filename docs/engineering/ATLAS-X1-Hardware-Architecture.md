# ATLAS X1 Hardware Architecture

## 1. Top-level partition

ATLAS X1 is divided into these hardware domains:

- Compute/networking SoC
- DDR memory
- Independent AtlasOS storage domain
- Independent OpenWrt storage domain
- Wi-Fi 7 radio/RF domain
- Multi-gig Ethernet/SFP+ domain
- Dual USB4 Type-C domain
- Security/secure-element domain
- Power-management domain
- Thermal-management domain
- Display/input/indicator domain
- Factory-test/debug domain

## 2. Functional topology

                     +----------------------+
                     |   DC Power Input     |
                     +----------+-----------+
                                |
                         +------+------+
                         | Power Tree  |
                         +------+------+
                                |
        +-----------------------+------------------------+
        |                       |                        |
   +----v-----+            +----v-----+            +-----v------+
   | Network  |            | Wi-Fi 7  |            | USB4 x2    |
   | SoC      |<---------->| radios   |            | Type-C     |
   +----+-----+            +----------+            +------------+
        |
  +-----+-------------------+--------------------+
  |                         |                    |
+--v---+                +----v----+          +----v----+
| DDR  |                | Ethernet|          | SFP+ x2 |
+------+                | switch  |          +---------+
                        +----+----+
                             |
                         RJ45 LAN x4

        +-------------------+-------------------+
        |                                       |
 +------v------+                         +------v------+
 | AtlasOS     |                         | OpenWrt     |
 | NOR + NAND  |                         | NOR + NAND  |
 +-------------+                         +-------------+
                                               /
         ------------- Boot manager ----------/
                         |
                    HW selector
                 Atlas / Auto / OWRT

## 3. Processor selection requirements

The final SoC must provide, directly or through validated companion controllers:

- Quad-core 64-bit ARM compute
- Hardware packet acceleration/NAT
- Cryptographic acceleration
- Secure boot/root-of-trust integration
- PCIe Gen4 capability
- High-speed DMA
- Sufficient Ethernet interfaces for the selected switch architecture
- Memory controller supporting the selected 8 GB memory technology
- Linux/OpenWrt BSP maturity
- Ten-year lifecycle availability target
- Industrial-quality documentation and reference design support

Decision gate: do not freeze the PCB until the SoC, DDR topology, Ethernet switch, Wi-Fi chipset, PCIe lane map and USB4 architecture are jointly validated.

## 4. Interface budget

| Domain | Required interface |
|---|---|
| Memory | 8 GB DDR4/LPDDR4X, final after SoC selection |
| Wi-Fi | PCIe/SoC-native interfaces as required by selected radio |
| Ethernet | 4 x 5GbE RJ45 + 2 x 10GbE SFP+ |
| USB | 2 x USB4 Type-C |
| Storage A | SPI NOR + NAND |
| Storage B | SPI NOR + NAND |
| Display | OLED controller interface |
| Security | Secure element, preferably I2C/SPI |
| Debug | UART/JTAG/SWD as supported |
| Thermal | PWM fan + tachometer + temperature sensors |

## 5. Isolation principle

The two operating-system domains shall remain electrically/logically independent wherever practical. The boot selector and recovery controller must not depend on a running OS for basic selection and recovery.

Shared resources are limited to infrastructure such as power, chassis, display, fan and selected networking peripherals. Firmware ownership of shared peripherals must be explicitly defined before implementation.
