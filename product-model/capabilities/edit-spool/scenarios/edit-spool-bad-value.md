---
kind: validation
routes:
  web: Web
steps:
  - text: Types a negative number, or a color that is not six hex digits
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Grams left
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The value is not usable
    kind: condition
    entities: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product refuses and keeps the spool as it was
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Grams left
          - Color
    contexts:
      web:
        place: hub::dashboard::spools
---

# Refuse a value that cannot be right

## Trigger

A slip of the keyboard while editing a row.

## Outcome

The spool is unchanged.
