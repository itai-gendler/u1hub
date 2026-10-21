---
availability:
  - place: hub::dashboard
domain: dispatch
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#releaseWaitersOf
  - kind: code
    role: implementation
    target: modules/dispatch.js#pruneBundles
---

# Remove a job

Taking a job out of Dispatch.
