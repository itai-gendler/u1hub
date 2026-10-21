---
availability:
  - place: hub::dashboard
domain: dispatch
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#reconcileFrozen
---

# Lock the plan

Freezing the times on screen so the board stops reshuffling on every refresh.
