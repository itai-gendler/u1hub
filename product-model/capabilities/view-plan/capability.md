---
availability:
  - place: hub::dashboard
domain: dispatch
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#pickStart
  - kind: code
    role: implementation
    target: modules/dispatch.js#queueBedClears
  - kind: code
    role: implementation
    target: modules/dispatch.js#findContention
  - kind: code
    role: implementation
    target: modules/dispatch.js#swapsFor
  - kind: code
    role: implementation
    target: public/modules/dispatch-ui.js
---

# View the plan

The Dispatch timeline: every printer's lane with what is running and every planned copy, recomputed as printers finish and pushed to the page as it changes.
