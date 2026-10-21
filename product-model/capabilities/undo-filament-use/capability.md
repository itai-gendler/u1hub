---
availability:
  - place: hub::dashboard
domain: spools
references:
  - kind: code
    role: implementation
    target: modules/resources.js#register
  - kind: code
    role: implementation
    target: modules/spoolman.js#register
---

# Undo a filament use

Undo on a line under Filament used by finished prints, for a deduction that got it wrong.
