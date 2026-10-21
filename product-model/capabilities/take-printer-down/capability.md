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
    target: modules/logbook.js#register
---

# Take a printer down for maintenance

Marking a printer out of service on purpose, which is different from a printer that does not answer. Nothing new is planned or sent to it until it comes back.
