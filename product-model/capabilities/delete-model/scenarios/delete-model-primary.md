---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Delete on a model card and confirms Delete for good
    kind: actor
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts:
          - File
          - Name
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product deletes the file and drops its attributes and gcode links
    kind: product
    actor: farm-operator
    entities:
      - entity: model
        effect: removes
    contexts:
      web:
        place: hub::dashboard::models
---

# Delete a model file

## Trigger

A model is not wanted.

## Outcome

The file is gone from disk and from the shelf.
