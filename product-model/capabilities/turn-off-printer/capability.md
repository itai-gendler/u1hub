---
availability:
  - place: hub::dashboard
domain: dash
references:
  - kind: code
    role: implementation
    target: modules/power.js#plugGuardState
  - kind: code
    role: implementation
    target: modules/power.js#plugSet
---

# Turn a printer off

Switching off a printer's smart plug from its card. The Hub's own Off never cuts power mid-print; the physical button and the plug's own app are outside its reach.
