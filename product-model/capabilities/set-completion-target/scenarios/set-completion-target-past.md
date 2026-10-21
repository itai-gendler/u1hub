---
kind: validation
routes:
  web: Web
steps:
  - text: Picks a moment that has passed and presses Set
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product refuses; the target is unchanged
    kind: product
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: reads
        facts:
          - Completion target
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Refuse a target in the past

## Trigger

A wrong date.

## Outcome

No report that marks everything missed.
