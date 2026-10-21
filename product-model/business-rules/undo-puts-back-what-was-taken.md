---
appliesTo:
  - type: capability
    id: undo-filament-use
  - type: entity
    id: filament-use
    effect: changes
    to: Undone
references:
  - kind: code
    role: implementation
    target: modules/resources.js#register
  - kind: code
    role: implementation
    target: modules/spoolman.js#register
---

# Undo puts back exactly what was taken, once

Undo adds each roll's deducted grams back and keeps the record, marked undone. Grams that reached Spoolman are taken back out of it too, even after write-back is turned off.
