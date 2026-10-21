---
availability:
  - place: hub::dashboard
domain: dash
references:
  - kind: code
    role: implementation
    target: modules/klipper.js
  - kind: code
    role: implementation
    target: public/app.js#klipperHref
---

# Open a printer's own page

Clicking a printer's name to open its full Klipper interface (Fluidd) in a new tab, with no IP address to type.
