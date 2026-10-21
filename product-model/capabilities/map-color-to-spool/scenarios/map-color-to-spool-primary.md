---
kind: primary
routes:
  web: Web
steps:
  - text: Picks a spool for a color's row
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Color name
          - Brand
      - entity: color-mapping
        effect: reads
        facts:
          - Slicer color
    contexts:
      web:
        place: hub::dashboard::resources
  - text: The Product pins that color to the spool, ahead of any automatic match
    kind: product
    actor: farm-operator
    entities:
      - entity: color-mapping
        effect: creates
        facts:
          - Slicer color
          - Spool
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::resources
---

# Pin a color to a roll

## Trigger

The slicer's placeholder blue is really the Galaxy Blue on the shelf.

## Outcome

Every scheduled job using that color counts against that spool.
