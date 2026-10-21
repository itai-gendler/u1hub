---
appliesTo:
  - type: capability
    id: add-job
  - type: entity
    id: job
    effect: creates
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#createJob
---

# A file waits in Dispatch only once

A file that already has a queued job outside a bundle is not added as a second job; more copies go onto the job that is waiting. A file whose copy is printing may be added again.
