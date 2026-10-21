---
domain: resources
references:
  - kind: code
    role: implementation
    target: modules/resources.js#matchSpool
---

# Color mapping

A slicer color pinned to one spool on the Resources tab, so every job that prints that color counts against that roll.

## Information kept

- **Slicer color** — The color as the slicer wrote it.
- **Spool** — The spool it counts against.
