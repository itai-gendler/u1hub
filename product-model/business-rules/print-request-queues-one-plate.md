---
appliesTo:
  - type: capability
    id: request-print
  - type: capability
    id: open-in-orca
  - type: capability
    id: link-gcode
references:
  - kind: code
    role: implementation
    target: modules/models.js#autoDispatch
---

# A print request queues one print of its plate

When a requested model's gcode exists, exactly one print of it goes into Dispatch. The x number in the gcode's name is how many pieces are on that one plate; it is recorded on the request, never turned into more prints.
