---
availability:
  - place: hub::dashboard
domain: dispatch
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#completeCopy
  - kind: code
    role: implementation
    target: modules/dispatch.js#endedWithout
  - kind: code
    role: implementation
    target: modules/dispatch.js#recordRun
  - kind: code
    role: implementation
    target: modules/dispatch.js#learnedFor
---

# Track job copies

What Dispatch does on its own as the printers report in: claim prints of queued files as they start, count copies as they complete, free a printer whose print ended without completing, and learn how long files really take.
