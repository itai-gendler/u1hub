---
kind: primary
routes:
  web: Web
steps:
  - text: Unticks deduct automatically, or ticks it again
    kind: actor
    actor: farm-operator
    entities:
      - entity: inventory-settings
        effect: reads
        facts:
          - Deduct automatically
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product keeps the choice for every print that finishes from now on
    kind: product
    actor: farm-operator
    entities:
      - entity: inventory-settings
        effect: changes
        facts:
          - Deduct automatically
    contexts:
      web:
        place: hub::dashboard::spools
---

# Stop deducting grams

## Trigger

The shelf is weighed by hand and should not be touched.

## Outcome

Finished prints leave the grams alone while it is off.
