# ATLAS X1 Platform Candidate Round 2

## 1. Broadcom BCM4916 + BCM6726/BCM67263

Broadcom's current documentation identifies BCM4916 as an active quad-core ARMv8 64-bit residential networking processor with DDR3/DDR4, integrated 10/5/2.5GbE PHY, three USXGMII ports, four PCIe controllers, dual USB, packet-processing acceleration and secure boot/TrustZone.

Broadcom's BCM6726/BCM67263 family provides 4x4 Wi-Fi 7 radio platforms covering the 2.4/5/6 GHz bands, with 320 MHz and 4096-QAM capability.

### Why this is important

This family is a better architectural match to the X1 than the previously reviewed single-chip platforms because it naturally supports a split design:

BCM4916
  |
  +-- BCM6726 / BCM67263 Wi-Fi 7 radios
  |
  +-- USXGMII / Ethernet fabric
  |
  +-- PCIe expansion
  |
  +-- DDR4
  |
  +-- secure boot

### Blocking unknown

Broadcom's public BCM4916 material does not state the PCIe generation in the currently accessible product documentation.

Therefore:

**BCM4916 is a high-priority candidate, but PCIe Gen4 is NOT confirmed.**

It must not be selected until Broadcom confirms:
- PCIe generation;
- lane width;
- simultaneous controller availability;
- lane sharing with Ethernet/Wi-Fi;
- 8 GB DDR4 topology;
- Linux/BSP access appropriate for ATLAS;
- secure-boot documentation;
- commercial lifecycle.

## 2. Wi-Fi architecture

A tri-band X1 design would require a radio allocation covering:

- 2.4 GHz;
- 5 GHz;
- 6 GHz.

Broadcom's public Wi-Fi 7 portfolio includes 4x4 BCM6726 and BCM67263 devices. The exact band assignment and simultaneous operation must be established from the vendor reference design.

## 3. Ethernet architecture

BCM4916 exposes three USXGMII interfaces plus integrated 10/5/2.5GbE capability. This makes it a plausible host for an external multi-gig switch/fabric.

Candidate external PHY families include Marvell Alaska M devices capable of 5GbE and 10GbE operation.

## 4. Decision

Status: **HIGH-PRIORITY CANDIDATE — pending PCIe Gen4 confirmation.**

Do not freeze the schematic around BCM4916 until the PCIe question is resolved.
