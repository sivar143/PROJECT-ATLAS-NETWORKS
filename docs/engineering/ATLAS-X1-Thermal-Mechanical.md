# ATLAS X1 Thermal and Mechanical Design

## 1. Mechanical concept

Target enclosure:

- premium PC/ABS or equivalent engineering plastic
- RF-transparent regions where required
- internal structural frame
- removable dust filter
- replaceable PWM fan
- side exhaust
- bottom filtered intake
- accessible maintenance panel

## 2. Airflow

BOTTOM FILTERED INTAKE
          |
          v
    PWM CENTRIFUGAL/AXIAL FAN
          |
          v
   PRIMARY HEATSINK ZONE
          |
          v
  SECONDARY COMPONENT ZONE
          |
     +----+----+
     |         |
 SIDE EXHAUST SIDE EXHAUST

## 3. Thermal zones

### Zone A — primary heat

- networking SoC
- Ethernet switch/PHY
- major networking controllers

### Zone B — secondary heat

- USB4 controllers
- PMICs
- supporting high-speed controllers

### Zone C — RF

Keep RF devices within the selected radio vendor's thermal and layout recommendations.

## 4. TIM

PTM7950 or equivalent phase-change material is the baseline where mechanically suitable. The final interface thickness, compression and contact pressure must be determined from the selected package/heatsink geometry.

## 5. Thermal sensors

Monitor at minimum:

- SoC
- Ethernet/switch hot spot
- radio hot spots where telemetry is available
- USB4 controllers
- intake/ambient
- exhaust
- fan tachometer

## 6. Mechanical service

The fan and filter shall be replaceable without destroying the enclosure. Fasteners should be reusable where practical. The maintenance design must avoid placing serviceable components behind permanently bonded cosmetic parts.

## 7. Acoustic target

The engineering target is quiet residential operation. Final dBA limits must be established after thermal load testing and acoustic testing rather than guessed before the fan/thermal solution is known.

## 8. Mechanical CAD deliverables

Required later:

- master assembly
- enclosure top
- enclosure bottom
- internal frame
- fan bracket
- heatsink assemblies
- filter carrier
- antenna mounts
- connector panel
- OLED window
- power button
- PCB mounting system
- exploded assembly drawing
- service drawing
