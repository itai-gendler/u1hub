---
appliesTo:
  - type: capability
    id: view-plan
  - type: capability
    id: print-on-best-printer
  - type: capability
    id: claim-running-prints
  - type: capability
    id: track-job-copies
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#maintOf
---

# A printer down for maintenance gets no new work

Nothing is planned on, chosen for, or claimed by a printer taken down for maintenance; a print already on its bed is left alone. A printer that does not answer is offline, which is a different thing.
