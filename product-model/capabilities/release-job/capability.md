---
availability:
  - place: hub::dashboard
domain: dispatch
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#register
---

# Release a job

Detaching a job from the printer it is wrongly attached to, so it can be matched again against what the printers report.
