---
availability:
  - place: hub::dashboard
domain: dispatch
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#dayWindow
  - kind: code
    role: implementation
    target: modules/dispatch.js#dayWindows
  - kind: code
    role: implementation
    target: public/modules/dispatch-ui.js
---

# Change attended hours

The attended hours panel: when someone is around to swap spools and clear beds, as a standing week or for one week, plus when jobs may finish and what a printer does with its rolls after a print.
