---
availability:
  - place: hub::dashboard
domain: resources
references:
  - kind: code
    role: implementation
    target: modules/resources.js#matchSpool
  - kind: code
    role: implementation
    target: public/modules/resources-ui.js
---

# Map a color to a spool

Pinning a slicer color to one spool on the Resources tab, when the automatic match is wrong or missing.
