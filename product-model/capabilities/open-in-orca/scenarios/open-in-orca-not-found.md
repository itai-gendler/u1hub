---
kind: validation
routes:
  web: Web
steps:
  - text: Presses Open in Orca on a model card
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
  - text: Snapmaker Orca is not at the location set
    kind: condition
    entities:
      - entity: models-settings
        effect: reads
        facts:
          - Orca location
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product says where it looked and to set the path
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::models
---

# Orca is not where the Hub looks

## Trigger

Orca is installed somewhere else.

## Outcome

Nothing is launched.
