---
availability:
  - place: hub::dashboard
domain: resources
references:
  - kind: code
    role: implementation
    target: modules/resources.js#rollup
  - kind: code
    role: implementation
    target: modules/resources.js#buildRows
  - kind: code
    role: implementation
    target: modules/resources.js#matchSpool
  - kind: code
    role: implementation
    target: public/modules/resources-ui.js
---

# View filament needs

The Resources tab: for everything Dispatch has scheduled, how much filament of each color is needed, how much is on the shelf, and what to buy, shortfall first.
