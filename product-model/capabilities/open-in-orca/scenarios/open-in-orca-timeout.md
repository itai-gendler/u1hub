---
kind: edge
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
  - text: The Product launches Orca and watches the gcode folder
    kind: product
    actor: farm-operator
    entities:
      - entity: orca-session
        effect: creates
        to: Watching
        facts:
          - Model file
          - Opened at
    contexts:
      web:
        place: hub::dashboard::models
  - text: Nothing is saved within half an hour
    kind: condition
    entities: []
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product stops watching
    kind: product
    actor: farm-operator
    entities:
      - entity: orca-session
        effect: changes
        from: Watching
        to: Timed out
        facts: []
    contexts:
      web:
        place: hub::dashboard::models
---

# Nothing is saved

## Trigger

Orca was closed without saving.

## Outcome

The session ends; nothing is linked.
