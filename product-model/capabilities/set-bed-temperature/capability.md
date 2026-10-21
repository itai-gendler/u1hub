---
availability:
  - place: hub::dashboard
domain: dash
references:
  - kind: code
    role: implementation
    target: core/telemetry.js
  - kind: code
    role: implementation
    target: public/app.js#setBed
---

# Set bed temperature

Setting or turning off a printer's bed heater from its card.
