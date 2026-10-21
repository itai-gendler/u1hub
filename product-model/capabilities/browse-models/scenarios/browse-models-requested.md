---
kind: alternate
routes:
  web: Web
steps:
  - text: Filters the shelf to Requested
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product shows every model marked for print in 3MF Explorer, waiting or already queued with its piece count
    kind: product
    actor: farm-operator
    entities:
      - entity: print-request
        effect: reads
        facts:
          - Designer
          - Title
          - Requested at
          - Gcode
          - Pieces
      - entity: model
        effect: reads
        facts:
          - Plate render
      - entity: 3mf-explorer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::models
---

# See what was marked for print

## Trigger

Someone browsing 3MF Explorer asked for prints.

## Outcome

The requests are on screen, each one either waiting for its gcode or already in Dispatch.
