# ATLAS X1 Preliminary Power Budget

## Status

Engineering budget, not a final adapter specification.

## 1. Budget method

Use:

P_total = P_compute + P_memory + P_WiFi + P_Ethernet + P_USB4 + P_storage + P_power_losses + P_fan + P_margin

A 25–30% system design margin should be retained until measured EVT data is available.

## 2. Budget placeholders

| Domain | Planning allocation | Status |
|---|---:|---|
| Networking SoC / CPU | 15 W | preliminary |
| Wi-Fi 7 radio/RF | 12 W | preliminary |
| Ethernet switch/fabric | 8 W | preliminary |
| 4 × 5GbE PHY | 12 W | preliminary |
| 2 × SFP+ subsystem | 6 W | preliminary, excluding module-specific external power |
| USB4 controller + Type-C | 10 W | preliminary |
| DDR | 5 W | preliminary |
| Storage/security/UI | 3 W | preliminary |
| Fans/sensors | 3 W | preliminary |
| DC/DC losses | 8 W | preliminary |
| Engineering margin | 18 W | preliminary |
| **Planning total** | **100 W** | **not final** |

## 3. Important USB-C policy

The X1 is a router, not a multi-port charging station. USB-C VBUS source power must therefore be constrained by system thermal and adapter capability.

The PD controller may support a much higher theoretical PD range than the product will advertise.

## 4. Adapter target

Do not freeze the adapter wattage from the current 100 W planning number.

The final adapter should be selected after:
1. SoC selection;
2. Wi-Fi power measurement;
3. Ethernet PHY measurement;
4. USB4 load testing;
5. fan startup/transient measurement;
6. worst-case simultaneous-load measurement.

## 5. Power validation

EVT measurements:
- startup peak;
- steady-state idle;
- routing-only;
- Wi-Fi-only;
- Ethernet-only;
- USB4 sustained;
- maximum simultaneous load;
- thermal steady state;
- brownout/recovery;
- adapter disconnect/reconnect.
