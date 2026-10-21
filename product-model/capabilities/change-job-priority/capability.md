---
availability:
  - place: hub::dashboard
domain: dispatch
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#register
---

# Change a job's priority

A job's 1 to 5 priority, 5 running first among jobs that share a deadline.
