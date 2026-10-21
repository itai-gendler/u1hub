---
appliesTo:
  - type: capability
    id: view-plan
  - type: capability
    id: change-job-priority
  - type: capability
    id: set-completion-target
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#register
---

# Deadlines come before priority

The plan runs the earliest deadline first; priority 1 to 5 only orders jobs that share a deadline, then the oldest job goes first. A job's deadline is its own or its bundle's, whichever is earlier; the completion target applies only to jobs with neither.

## Rationale

A missed deadline is a broken promise; a priority is a preference.
