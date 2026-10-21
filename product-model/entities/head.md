---
relations:
  - entity: spool
    verb: holds
    cardinality: one-to-one
references:
  - kind: code
    role: implementation
    target: core/fleet.js#decodeHeads
  - kind: code
    role: implementation
    target: core/filament.js
---

# Head

One of a printer's toolheads, T1 to T4 on a U1. What is loaded in it is what the printer reports from its own filament settings; a single-extruder printer shows none.

## Information kept

- **Number** — T1 to T4.
- **Loaded** — Whether filament is in the head.
- **Loaded color** — The color set for the loaded filament, or the colors of a multi-color spool.
- **Material** — The filament material set for the head, such as PLA or PETG.
- **Official spool** — Yes when an official Snapmaker RFID spool is loaded; its color and material come from the tag and show with a lock.
