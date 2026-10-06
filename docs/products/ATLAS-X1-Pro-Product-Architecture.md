# ATLAS X1 Pro — Product Architecture

## Role

Higher-performance router above X1.

## Target architecture

- higher-throughput networking SoC;
- larger memory budget;
- greater multi-gig wired capacity;
- enhanced 10GbE/25GbE expansion where justified;
- more powerful Wi-Fi 7 radio architecture;
- expanded storage;
- stronger thermal system;
- optional additional PCIe/USB expansion.

## Reuse from X1

- secure boot and provisioning
- dual-OS concept where practical
- AtlasOS
- diagnostics
- policy model
- management APIs
- cloud/mobile integration

## Design rule

X1 Pro must be an independently validated platform. It must not become a collection of unverified X1 feature additions.
