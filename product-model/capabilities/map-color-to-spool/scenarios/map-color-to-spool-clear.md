---
kind: alternate
routes:
  web: Web
steps:
  - text: Picks the automatic choice for a mapped color's row
    kind: actor
    actor: farm-operator
    entities:
      - entity: color-mapping
        effect: reads
        facts:
          - Slicer color
          - Spool
    contexts:
      web:
        place: hub::dashboard::resources
  - text: The Product drops the pin
    kind: product
    actor: farm-operator
    entities:
      - entity: color-mapping
        effect: removes
    contexts:
      web:
        place: hub::dashboard::resources
---

# Go back to the automatic match

## Trigger

The pin is no longer right.

## Outcome

The color is matched automatically again.
