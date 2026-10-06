# ATLAS X1 SoC and High-Speed Lane Budget

## 1. Objective

Define the minimum high-speed fabric that the final SoC/platform must expose.

## 2. Required external links

| Link | Count | Minimum target | Preferred |
|---|---:|---:|---|
| USB4 host | 1 controller | PCIe Gen4 x4 | PCIe Gen4 x4 dedicated |
| 10GbE SFP+ | 2 | 10Gb/s SerDes each | 10GbE/25GbE capable SerDes |
| 5GbE copper | 4 | 5GBASE-T | 5G/10G capable |
| Wi-Fi 7 | 1 platform | vendor-specific high-speed host link | integrated or dedicated high-bandwidth fabric |
| Storage | 4 domains | SPI/NAND | independent controllers/buses |
| Debug | 1 | UART + JTAG | authenticated production debug |

## 3. Important bandwidth rule

The four 5GbE ports cannot be treated as four independent 5Gb/s CPU links without considering switch architecture.

Preferred architecture:

SoC / network processor
       |
       | high-bandwidth Ethernet fabric
       v
+-------------------+
| Multi-gig switch  |
+--+--+--+--+--+---+
   |  |  |  |  |  |
 5G  5G  5G  5G 10G 10G
 RJ45...          SFP+ SFP+

The switch should perform local L2 forwarding without forcing every packet through the CPU.

## 4. USB4 requirement

USB4 controller:

PCIe Gen4 x4
      |
      v
ASM4242-class host
   +------+------+
   |             |
 USB4-A        USB4-B

The x4 link should remain dedicated unless SI/performance analysis proves that controlled sharing is acceptable.

## 5. Storage isolation

AtlasOS:
- NOR-A
- NAND-A

OpenWrt:
- NOR-B
- NAND-B

The boot/recovery controller must be capable of selecting the correct domain before OS execution.

## 6. Selection gate

A candidate SoC is rejected if:
- PCIe Gen4 x4 cannot be provided;
- DDR4/LPDDR4X cannot reach 8 GB;
- secure boot is unavailable;
- required Ethernet SerDes cannot be exposed;
- Linux/OpenWrt BSP support is insufficient.

