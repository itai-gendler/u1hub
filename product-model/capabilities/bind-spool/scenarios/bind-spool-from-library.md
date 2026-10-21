---
kind: primary
routes:
  web: Web
steps:
  - text: Searches the filament library by color, brand or material, picks a match and presses Bind this spool
    kind: actor
    actor: farm-operator
    entities:
      - entity: filament-library
        effect: reads
        facts:
          - Swatches
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product makes the spool from that pick, with its measured color and recommended temperatures, and attaches the tag
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: creates
        to: On the shelf
        facts:
          - Brand
          - Material
          - Variant
          - Color name
          - Color
          - Hot end temperature
          - Bed temperature
          - Tags
          - Origin
      - entity: filament-library
        effect: reads
        facts:
          - Swatches
    contexts:
      web:
        place: hub::dashboard::spools
---

# Bind a tag to a filament from the library

## Trigger

A new tagged roll is one the library knows.

## Outcome

The spool is on the shelf; tapping its tag opens its card from now on.
