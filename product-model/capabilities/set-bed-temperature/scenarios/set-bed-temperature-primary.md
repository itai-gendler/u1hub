---
kind: primary
routes:
  web: Web
steps:
  - text: Types a temperature on a card and presses Set
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
          - Bed temperature
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product sets the bed's target without waiting for it
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Bed temperature
    contexts:
      web:
        place: hub::dashboard::dash
---

# Warm the bed

## Trigger

The bed should be warm before the next print.

## Outcome

The card shows the new target as the bed heats.
