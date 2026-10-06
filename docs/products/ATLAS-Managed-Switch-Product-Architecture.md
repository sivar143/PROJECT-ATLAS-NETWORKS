# ATLAS Managed Switch — Product Architecture

## Role

Managed multi-gig switch family for homes, SOHO and advanced users.

## Core capabilities

- VLAN
- QoS
- link aggregation where supported
- port isolation
- STP/RSTP/MSTP as appropriate
- LLDP
- DHCP snooping where supported
- ACLs
- PoE variants where required
- local web management
- ATLAS controller integration

## Hardware families

The design should be modular around port-density classes rather than one fixed model.

Candidate families:

- 8-port compact
- 16-port
- 24-port
- 48-port

Speed combinations remain TBD based on target market and silicon availability.

## Design priorities

Reliability, silent/low-noise operation, thermal efficiency, surge/ESD protection and long lifecycle.
