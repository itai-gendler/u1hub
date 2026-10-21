---
kind: validation
routes:
  web: Web
steps:
  - text: Presses Convert to U1 on a model card
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
  - text: A U1 copy is already next to it
    kind: condition
    entities:
      - entity: model
        effect: reads
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product refuses and offers to open the U1 copy instead
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::models
---

# Already converted

## Trigger

The model was converted before.

## Outcome

Nothing is overwritten.
