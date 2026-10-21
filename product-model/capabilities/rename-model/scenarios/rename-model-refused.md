---
kind: validation
routes:
  web: Web
steps:
  - text: Presses Rename on a model card
    kind: actor
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::models
  - text: The designer or the name is unknown, or a file is already at the target
    kind: condition
    entities:
      - entity: model
        effect: reads
        facts:
          - Designer
          - Name
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product says to set the designer or name under Attributes, or to change the name or delete one of them
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::models
---

# Refuse a rename that cannot be done

## Trigger

The model's identity is incomplete, or the target is taken.

## Outcome

The file stays where it is.
