---
appliesTo:
  - type: capability
    id: turn-off-printer
  - type: entity
    id: printer
    effect: changes
    facts:
      - Plug power
references:
  - kind: code
    role: implementation
    target: modules/power.js#plugGuardState
---

# The Hub never cuts power to a printer that is printing

Off is refused while the printer is printing or paused, and also when the Hub cannot confirm it is idle. Turning a plug on is always allowed.

## Rationale

Failing safe leaves a printer on; failing the other way ruins a print.
