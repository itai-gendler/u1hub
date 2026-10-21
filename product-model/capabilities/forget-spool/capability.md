---
availability:
  - place: hub::dashboard
domain: spools
references:
  - kind: code
    role: implementation
    target: rfid.js#unassignSpool
  - kind: code
    role: implementation
    target: modules/resources.js#reconcileInventory
---

# Forget a spool

Removing a roll from the Hub, with every tag that pointed at it.
