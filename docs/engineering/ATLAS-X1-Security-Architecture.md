# ATLAS X1 Security Architecture

## 1. Root of trust

The device shall use a hardware-backed trust chain covering:

- immutable boot/root key material
- signed bootloader
- signed OS images
- secure configuration
- secure element/device identity

## 2. Secure element

Use a dedicated secure element or equivalent hardware root of trust for:

- device identity
- certificate/private-key storage
- attestation material
- protected provisioning

The exact device is TBD pending interface, lifecycle and manufacturing requirements.

## 3. Secure boot

Boot chain:

ROM / immutable root
      |
verified first-stage boot
      |
verified bootloader
      |
verified OS slot
      |
verified kernel/rootfs
      |
runtime integrity controls

## 4. Anti-rollback

Firmware metadata shall include a monotonic security version. Images below the accepted security version must be rejected unless an authenticated manufacturing recovery procedure explicitly authorizes rollback.

## 5. Key provisioning

Factory provisioning must:

- generate or inject device-unique identity;
- protect private keys;
- bind certificates to device identity;
- record provisioning result;
- prevent duplicate identities.

## 6. Network security

AtlasOS target features include:

- WPA3
- stateful firewall
- IPv6 firewall
- WireGuard
- IPsec
- OpenVPN
- DNS-over-HTTPS
- DNS-over-TLS
- device quarantine
- automatic security updates

Feature availability depends on final CPU performance, memory, licensing and software implementation.

## 7. Debug security

Engineering debug ports are required during development but must be locked, authenticated or disabled in production as appropriate.

## 8. Threat-model priorities

Highest-priority assets:

1. device identity/private keys
2. firmware integrity
3. user credentials
4. network configuration
5. traffic-routing policy
6. update mechanism
7. recovery mechanism

Security verification must include both normal operation and compromised-firmware/recovery scenarios.
