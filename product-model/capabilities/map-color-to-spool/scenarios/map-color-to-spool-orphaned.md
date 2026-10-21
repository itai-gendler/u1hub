---
kind: edge
routes:
  web: Web
steps:
  - text: Opens Resources
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::resources
  - text: A color is pinned to a spool that is no longer on the shelf
    kind: condition
    entities:
      - entity: color-mapping
        effect: reads
        facts:
          - Spool
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::resources
  - text: The Product marks the row orphaned and names what went missing, keeping the pin rather than guessing a new match
    kind: product
    actor: farm-operator
    entities:
      - entity: color-mapping
        effect: reads
        facts:
          - Slicer color
    contexts:
      web:
        place: hub::dashboard::resources
---

# A pinned spool was forgotten

## Trigger

A roll was swapped for another brand and the old one forgotten.

## Outcome

The operator sees why the row lost its spool and can pin the new one.
