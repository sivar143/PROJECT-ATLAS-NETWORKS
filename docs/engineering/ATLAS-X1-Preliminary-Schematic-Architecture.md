# ATLAS X1 Preliminary Schematic Architecture

## Status

Architecture-level schematic partition. Not a fabrication schematic.

## Sheet hierarchy

1. 00_TOP_LEVEL
2. 01_POWER_INPUT
3. 02_POWER_TREE
4. 03_SOC_DDR
5. 04_WIFI7_RF
6. 05_ETHERNET_SWITCH
7. 06_5GBE_PHY
8. 07_SFP_PLUS
9. 08_USB4_A
10. 09_USB4_B
11. 10_STORAGE_ATLAS
12. 11_STORAGE_OPENWRT
13. 12_SECURITY
14. 13_BOOT_SELECTOR
15. 14_OLED_UI
16. 15_FAN_THERMAL
17. 16_FACTORY_TEST
18. 17_DEBUG

## Top-level connectivity

[DC INPUT]
    |
[Protection]
    |
[Main Power Tree]
    |
    +-------------------+
    |                   |
  [SoC]              [High-current rails]
    |
    +-- DDR4 / LPDDR4X
    |
    +-- Ethernet fabric
    |      +-- 4 x 5GbE PHY -> RJ45
    |      +-- 2 x 10GbE SerDes -> SFP+
    |
    +-- PCIe Gen4 x4 -> USB4 controller -> Type-C A/B
    |
    +-- SPI/I/O -> AtlasOS storage
    |
    +-- SPI/I/O -> OpenWrt storage
    |
    +-- I2C/SPI -> secure element
    |
    +-- GPIO/I2C -> OLED/RGB button/fan controller
    |
    +-- UART/JTAG -> factory debug

## Power sheet

External DC
 -> fuse/eFuse
 -> TVS
 -> reverse-current protection
 -> EMI filter
 -> main buck rails
 -> point-of-load regulators/LDOs

The actual rail list must be generated from the selected SoC/radio/switch reference designs.

## Ethernet sheet

The preferred design is a dedicated switch/fabric so LAN-to-LAN traffic does not consume CPU bandwidth.

RJ45 path:

SoC/switch SerDes
 -> 5GbE PHY
 -> magnetics
 -> ESD
 -> RJ45

SFP+ path:

SoC/switch SerDes
 -> SFP+ cage
 -> high-speed ESD/EMI network
 -> module management I2C

## USB4 sheet

PCIe Gen4 x4
 -> USB4 host controller
 -> Type-C mux/PD controller
 -> retimer only if channel budget requires
 -> ESD
 -> Type-C connector

## Storage sheets

Each OS domain gets independent:
- boot NOR
- NAND
- reset/enable
- power gating where practical

## Security sheet

SoC secure boot root
 -> verified bootloader
 -> verified OS

Secure element
 -> device identity
 -> certificate/key operations
 -> manufacturing provisioning

## Factory test

Provide accessible test points for:
- input power
- major rails
- reset
- UART
- JTAG where permitted
- SPI/NAND
- Ethernet
- USB4
- secure element
- fan tach/PWM
- thermal sensors

## Rule

No detailed pin numbers or passive values may be frozen until the final SoC and companion ICs are selected.
