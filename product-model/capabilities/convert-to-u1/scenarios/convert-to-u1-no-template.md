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
  - text: There is no U1 template
    kind: condition
    entities:
      - entity: models-settings
        effect: reads
        facts:
          - U1 template
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product explains how to save one from Snapmaker Orca as u1_template.3mf in the models folder, or set its path
    kind: product
    actor: farm-operator
    entities:
      - entity: model
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::models
---

# No U1 template yet

## Trigger

Convert is tried for the first time.

## Outcome

Nothing is written.
