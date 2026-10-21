---
kind: primary
routes:
  web: Web
steps:
  - text: Presses edit on a spool, changes its brand, name, color or temperatures and saves
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Brand
          - Color name
          - Color
          - Hot end temperature
          - Bed temperature
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product updates the spool; a changed color no longer counts as the catalog's measured color
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: changes
        facts:
          - Brand
          - Material
          - Variant
          - Color name
          - Color
          - Hot end temperature
          - Bed temperature
          - Origin
    contexts:
      web:
        place: hub::dashboard::spools
---

# Correct a spool's identity

## Trigger

A refillable spool now holds a different filament, or a detail was wrong.

## Outcome

The spool reads right everywhere, with no forgetting and rescanning.
