# ATLAS Cloud Controller — Architecture

## Role

Centralized management plane for ATLAS networks.

## Responsibilities

- organization/site management
- device inventory
- configuration orchestration
- firmware lifecycle
- health dashboards
- event history
- alerts
- backup/restore of configuration
- RBAC
- audit logs
- fleet diagnostics
- license/subscription integration if introduced later

## Security boundary

The cloud controller must never require exposure of the LAN management plane directly to the public Internet. Devices should establish authenticated outbound control channels.

Local management must remain possible according to each product's design.
