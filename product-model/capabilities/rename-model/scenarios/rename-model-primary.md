---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Rename on a model card, checks the target shown and presses Move and rename
    kind: actor
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts:
          - File
          - Designer
          - Name
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product moves the file to Designer, then Name, then Designer - Name, carrying its attributes and gcode links with it
    kind: product
    actor: farm-operator
    entities:
      - entity: model
        effect: changes
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::models
---

# File a model by the convention

## Trigger

A download landed with a messy name.

## Outcome

The model is filed the same way as the rest of the shelf, and nothing that pointed at it is lost.
