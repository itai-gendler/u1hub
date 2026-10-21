---
availability:
  - place: hub::dashboard
domain: dash
references:
  - kind: code
    role: implementation
    target: core/print.js
  - kind: code
    role: implementation
    target: public/app.js#skipObject
  - kind: code
    role: implementation
    target: public/app.js#plateSVG
---

# Skip an object

Skipping one object on a running plate while the rest keeps printing.
