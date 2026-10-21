---
appliesTo:
  - type: capability
    id: load-spool
  - type: capability
    id: forget-spool
references:
  - kind: code
    role: implementation
    target: rfid.js#unassignSpool
---

# A spool is loaded in one head at a time

Loading a spool records it in exactly one head: loading it elsewhere moves it, loading into an occupied head puts the occupant back on the shelf, and a forgotten spool stops being loaded.

## Rationale

Filament is physical.
