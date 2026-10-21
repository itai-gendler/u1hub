---
availability:
  - place: hub::dashboard
domain: dispatch
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#register
  - kind: code
    role: implementation
    target: public/modules/dispatch-ui.js
---

# Move a job

Move in a planned block's panel: pin a job to one printer, or hand the choice back to the planner.
