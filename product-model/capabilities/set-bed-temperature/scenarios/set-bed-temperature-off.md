---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses Off on a card
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
  - text: The Product sets the bed's target to zero
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

# Turn the bed off

## Trigger

A bed was left warm.

## Outcome

The bed cools.
