---
appliesTo:
  - type: capability
    id: view-plan
  - type: capability
    id: change-attended-hours
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#pickStart
---

# A copy starts only inside attended hours

Every planned copy starts inside an attended block. Under Finish jobs anytime it may run on after the block, and a later start is chosen only while the printer would otherwise sit full and waiting; under only while I am here it must also end inside one block.
