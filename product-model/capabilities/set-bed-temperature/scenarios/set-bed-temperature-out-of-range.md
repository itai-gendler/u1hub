---
kind: validation
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
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The temperature is above 120 °C or not a number
    kind: condition
    entities: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product refuses; the target is unchanged
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

# Refuse a temperature out of range

## Trigger

A typo in the field.

## Outcome

Nothing is sent.
