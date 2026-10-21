---
availability:
  - place: hub::dashboard
domain: models
references:
  - kind: code
    role: implementation
    target: modules/models.js#openSession
  - kind: code
    role: implementation
    target: modules/desktop.js
  - kind: code
    role: implementation
    target: modules/tuning.js
---

# Open in Orca

Opening a model in Snapmaker Orca on the Hub computer and watching the gcode folder for what Orca saves, so the new gcode is linked to the model and one tap from Dispatch. Only on the Hub computer's own screen: a phone does not offer it.
