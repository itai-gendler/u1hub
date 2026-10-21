---
availability:
  - place: hub::dashboard
domain: dispatch
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#register
  - kind: code
    role: implementation
    target: public/modules/dispatch-ui.js
---

# Clear the bed and start the next job

Bed cleared → next on a printer's lane: the Hub never starts a printer itself, so this tap is how the next planned copy reaches the printer. It hands over to the Dash, where the head mapping is confirmed and Print pressed.
