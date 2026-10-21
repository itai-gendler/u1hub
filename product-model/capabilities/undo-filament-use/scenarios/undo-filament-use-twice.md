---
kind: validation
routes:
  web: Web
steps:
  - text: Presses Undo on a line
    kind: actor
    actor: farm-operator
    entities:
      - entity: filament-use
        effect: reads
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The line is already undone
    kind: condition
    entities:
      - entity: filament-use
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product refuses
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::spools
---

# A line can be undone once

## Trigger

Undo is pressed on a line twice from two devices.

## Outcome

The grams go back once.
