---
kind: validation
routes:
  web: Web
steps:
  - text: Sets the sell floor to zero, or a rate above 100
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::settings
  - text: The Product refuses
    kind: product
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - Sell floor per gram
    contexts:
      web:
        place: hub::dashboard::settings
---

# A sell floor of zero

## Trigger

A sell floor typed as 0, or in cents instead of dollars.

## Outcome

The rates are unchanged.
