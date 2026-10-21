---
availability:
  - place: hub::dashboard
domain: models
references:
  - kind: code
    role: implementation
    target: modules/models.js#register
  - kind: code
    role: implementation
    target: modules/models.js#autoDispatch
---

# Link a gcode

Link gcode on a card: saying by hand which gcode files were sliced from a model, one at a time, since a multi-part model prints as several.
