# ATLAS X1 Boot, Storage and Recovery Architecture

## 1. Required storage domains

### Domain A — AtlasOS

- SPI NOR A: bootloader, recovery and immutable/verified boot metadata.
- NAND A: AtlasOS, configuration, logs and A/B firmware slots.

### Domain B — OpenWrt

- SPI NOR B: bootloader, recovery and immutable/verified boot metadata.
- NAND B: OpenWrt, configuration, logs and A/B firmware slots.

Each domain must be independently recoverable.

## 2. Hardware selector

Three positions:

1. AtlasOS
2. Automatic
3. OpenWrt

The selector must be sampled before normal OS execution. The selector is a boot-policy input, not a software UI setting.

## 3. Automatic mode

Automatic mode should boot the last known-good OS according to a persistent boot-health record.

Recommended state machine:

POWER ON
  |
Hardware validation
  |
Read boot policy
  |
Select OS
  |
Verify boot image
  |---- fail ----> alternate/recovery policy
  |
Boot
  |
Health confirmation
  |---- fail ----> mark failed + rollback
  |
RUNNING

## 4. Secure update

An update shall:

1. authenticate the package;
2. verify compatibility;
3. write only the inactive slot;
4. verify the written image;
5. update boot metadata atomically;
6. boot the new slot;
7. require health confirmation;
8. automatically revert on repeated boot failure.

## 5. Cross-recovery

Each OS shall have a controlled mechanism to repair the other OS, but cross-flashing must never permit an unverified image to replace a trusted boot image.

## 6. Factory reset

Factory reset must distinguish:

- user configuration reset;
- OS slot reset;
- full storage reinitialization;
- secure-key/device-identity preservation.

Device identity and manufacturing credentials must not be erased by an ordinary factory reset.

## 7. Debug/recovery

Expose a protected factory recovery interface such as UART/JTAG where supported. Production units shall disable or authenticate privileged debug access according to the security architecture.
