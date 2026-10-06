# ATLAS X1 Engineering Verification Plan

## 1. Verification gates

| Gate | Objective | Exit condition |
|---|---|---|
| EVT-0 | Architecture | Interfaces and assumptions reviewed |
| EVT-1 | Bring-up | Board boots both OS domains |
| EVT-2 | Core hardware | CPU, DDR, storage, Ethernet, USB4 operational |
| EVT-3 | RF | Wi-Fi 7 bring-up and initial RF validation |
| EVT-4 | Thermal | Sustained-load thermal limits met |
| DVT-1 | Reliability | 24x7 and stress validation |
| DVT-2 | Compliance | Pre-compliance issues closed |
| PVT | Production | Manufacturing test and yield validated |

## 2. Core tests

### Boot/recovery
- cold boot
- warm reboot
- forced power loss
- corrupted slot
- rollback
- selector mode changes
- recovery without network

### Storage
- read/write integrity
- power-loss behavior
- bad-block handling
- endurance sampling

### Networking
- 5GbE throughput
- SFP+ throughput
- VLAN
- QoS
- multi-WAN
- IPv4/IPv6
- firewall
- sustained routing/NAT

### USB4
- link training
- hot plug
- sustained storage throughput
- USB Ethernet
- modem
- error recovery

### Wireless
- each band
- MLO
- 320 MHz where legal/supported
- roaming
- coexistence
- range
- throughput
- thermal derating

### Thermal/reliability
- maximum traffic load
- simultaneous Wi-Fi/Ethernet/USB load
- fan failure behavior
- blocked-filter simulation
- ambient-temperature sweep
- long-duration burn-in

## 3. Pass/fail rule

Every test must have a measurable acceptance criterion before DVT. Tests without a numeric or observable pass/fail definition are not considered complete verification.
