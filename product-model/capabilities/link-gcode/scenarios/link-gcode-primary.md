---
kind: primary
routes:
  web: Web
steps:
  - text: Opens Link gcode on a model card and picks a gcode from the list
    kind: actor
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts:
          - File
      - entity: library-file
        effect: reads
        facts:
          - Name
          - Linked model
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product links the gcode to the model as verified
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: changes
        facts:
          - Linked model
          - Link verified
      - entity: model
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::models
---

# Link a gcode to its model

## Trigger

A gcode was sliced elsewhere, or an automatic link was a guess.

## Outcome

The model's printed count and its requests use the link.
