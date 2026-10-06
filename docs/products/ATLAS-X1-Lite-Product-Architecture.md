# ATLAS X1 Lite — Product Architecture

## Role

Lower-cost member of the ATLAS premium router family.

## Target architecture

- Wi-Fi 7 tri-band baseline where cost and regulatory constraints permit.
- Lower aggregate wired-port count than X1.
- Reduced USB expansion.
- Simplified thermal system while retaining serviceability.
- Common AtlasOS platform.
- Optional OpenWrt path where storage/security architecture permits.

## Reuse from X1

- security model
- update model
- management APIs
- diagnostics concepts
- IoT/guest segmentation
- mobile/cloud integration

## Deliberate reductions

- lower compute/storage capacity;
- fewer high-speed wired interfaces;
- simpler mechanical assembly;
- lower thermal capacity.

Exact specifications are TBD until the target cost and SoC/radio availability are established.
