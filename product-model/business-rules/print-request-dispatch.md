---
appliesTo:
  - type: entity
    id: print-request
    effect: changes
    to: Dispatched
permits:
  - actors:
      - farm-operator
  - actors:
      - 3mf-explorer
references:
  - kind: code
    role: implementation
    target: modules/models.js#autoDispatch
---

# The operator or 3MF Explorer moves a print request to Dispatched

A request moves to Dispatched as a consequence of a gcode for its model being linked, whoever's action made the link exist: Open in Orca or Link gcode by the operator, or a request from 3MF Explorer for a model already sliced.
