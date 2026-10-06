# ATLAS X1 Hardware Architecture

## 1. Top-level partition

ATLAS X1 is divided into these hardware domains:

- ARM network/application processor
- DDR memory
- Independent AtlasOS storage domain
- Independent OpenWrt storage domain
- Wi-Fi 7 radio/RF domain
- Multi-gig Ethernet switch/fabric
- 5GbE copper PHY domain
- 10GbE SFP+ SerDes domain
- Dual USB4 Type-C domain
- Security/secure-element domain
- Power-management domain
- Thermal-management domain
- Display/input/indicator domain
- Factory-test/debug domain

## 2. Architecture selection status

The project is currently between two candidate platform models:

### Model A — integrated networking SoC

Wi-Fi 7 + ARM + networking acceleration in one platform.

### Model B — split networking architecture

ARM processor/networking engine
       |
       +---- Ethernet switch/fabric
       |       +---- 4 x 5GbE PHY -> RJ45
       |       +---- 2 x 10GbE SerDes -> SFP+
       |
       +---- dedicated Wi-Fi 7 platform
       |
       +---- PCIe Gen4 x4 -> USB4 controller

Model B is being investigated because the currently evaluated integrated Wi-Fi 7 networking SoCs do not satisfy the PDS PCIe Gen4 requirement.

## 3. Interface budget

| Domain | Required interface |
|---|---|
| CPU | Quad-core 64-bit ARM |
| Memory | 8 GB DDR4/LPDDR4X |
| Wi-Fi | Tri-band Wi-Fi 7 |
| Ethernet | 4 x 5GbE RJ45 |
| SFP+ | 2 x 10GbE configurable WAN/LAN |
| USB | 2 x USB4 Type-C |
| USB host | PCIe Gen4 x4 target |
| Storage A | SPI NOR + NAND |
| Storage B | SPI NOR + NAND |
| Security | Secure element |
| UI | OLED + RGB button |
| Thermal | PWM fan + tachometer + sensors |
| Debug | UART + JTAG or SoC-supported secure debug |

## 4. Networking architecture

The preferred topology is:

                 +------------------+
                 | ARM Network CPU  |
                 +--------+---------+
                          |
                  High-speed fabric
                          |
                 +--------v---------+
                 | Ethernet Switch  |
                 +--+--+--+--+--+--+
                    |  |  |  |  |  |
                   5G 5G 5G 5G 10G 10G
                   RJ45 RJ45 RJ45 RJ45 SFP SFP

The switch should perform local forwarding so LAN-to-LAN traffic does not unnecessarily traverse the CPU.

## 5. USB4 architecture

                 PCIe Gen4 x4
                      |
                +-----v------+
                | USB4 Host  |
                | Controller |
                +--+-------+-+
                   |       |
                 USB4-A  USB4-B
                   |       |
                Type-C   Type-C

A retimer/redriver is only populated if the final channel analysis requires it.

## 6. Wi-Fi 7

The final Wi-Fi 7 platform must provide:
- 2.4 GHz;
- 5 GHz;
- 6 GHz;
- required spatial streams;
- MLO;
- 320 MHz where permitted;
- 4096-QAM;
- OFDMA;
- MU-MIMO;
- beamforming;
- regulatory control.

## 7. Storage

AtlasOS:
- NOR-A;
- NAND-A.

OpenWrt:
- NOR-B;
- NAND-B.

The boot selector and recovery controller must operate before normal OS execution.

## 8. Decision gate

Do not freeze the PCB until:
- platform model is selected;
- SoC/processor is selected;
- Wi-Fi platform is selected;
- Ethernet fabric is selected;
- USB4 host is selected;
- PCIe lane map is validated.
