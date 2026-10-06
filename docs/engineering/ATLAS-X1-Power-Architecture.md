# ATLAS X1 Power Architecture

## 1. Objectives

The power subsystem shall provide stable, protected rails for sustained 24x7 networking loads and transient-heavy USB/RF operation.

## 2. Preliminary rail tree

The exact voltages are intentionally left as TBD by selected silicon.

External DC input
      |
   Input fuse
      |
 TVS / surge protection
      |
 Reverse-polarity protection
      |
 EMI input filter
      |
 +----+-------------------------------+
 |                                    |
Main high-current buck               Auxiliary buck/LDOs
 |                                    |
 +-- SoC core / CPU                   +-- DDR
 +-- SoC I/O                          +-- NOR
 +-- Ethernet                         +-- NAND
 +-- Wi-Fi                            +-- secure element
 +-- USB4                             +-- OLED
 +-- SFP+                             +-- sensors/fan

## 3. Design requirements

- Size input stage for worst-case sustained load plus transient margin.
- Use independent protection for externally accessible interfaces.
- Keep noisy switching regulators physically separated from RF and high-speed SerDes.
- Provide current/voltage telemetry on major rails where practical.
- Provide power-good sequencing and brownout handling.
- Provide controlled shutdown/recovery behavior.
- Validate adapter selection for worldwide target mains regions.

## 4. USB-C power

USB4 Type-C ports require a dedicated, standards-compliant Type-C/PD architecture where power delivery or sourcing is enabled. The final design must define:

- source/sink role
- negotiated voltage/current
- over-current protection
- ESD protection
- VBUS discharge
- CC/PD controller
- cable/e-marker behavior
- thermal limits

No USB-C power rating is considered frozen until the selected controller and connector are validated.

## 5. Power sequencing

Power sequencing shall be derived from the selected SoC and radio reference designs. Required controls include:

- global reset
- rail enable dependencies
- DDR reset
- Wi-Fi reset
- Ethernet switch reset
- USB4 controller reset
- storage reset/strap requirements

## 6. Protection

At minimum evaluate:

- fuse/eFuse
- TVS
- reverse-current blocking
- over-voltage protection
- over-current protection
- short-circuit response
- thermal shutdown
- ESD at every user-accessible connector

## 7. Validation

Measure startup, shutdown, steady-state ripple, transient response, thermal rise and conducted/radiated noise at EVT.
