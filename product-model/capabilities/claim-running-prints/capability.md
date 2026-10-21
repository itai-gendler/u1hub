---
availability:
  - place: hub::dashboard
domain: dispatch
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#reconcile
  - kind: code
    role: implementation
    target: modules/dispatch.js#sameFile
---

# Claim running prints

Matching prints already running on the farm to queued jobs, so Dispatch stops planning work the farm is already doing. The Hub also does this on its own as prints start.
