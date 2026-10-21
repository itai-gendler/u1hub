---
availability:
  - place: hub::dashboard
references:
  - kind: code
    role: implementation
    target: core/records.js#pollPrintStarts
  - kind: code
    role: implementation
    target: core/records.js#fileContentHash
  - kind: code
    role: implementation
    target: core/records.js#loadoutSnapshot
---

# Record print history

What the Hub notes about prints on its own: when each file last started, and which spools were in the heads when it finished.
