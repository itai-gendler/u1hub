---
availability:
  - place: hub::dashboard
domain: dash
references:
  - kind: code
    role: implementation
    target: modules/power.js#plugSet
  - kind: code
    role: implementation
    target: public/app.js#setPower
---

# Turn a printer on

Switching on a printer's smart plug from its card, even while the printer is offline.
