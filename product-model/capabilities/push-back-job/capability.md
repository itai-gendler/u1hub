---
availability:
  - place: hub::dashboard
domain: dispatch
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#register
---

# Push back a job

Push back one in a planned block's panel: this job waits behind the next one in the plan, without moving it to another printer.
