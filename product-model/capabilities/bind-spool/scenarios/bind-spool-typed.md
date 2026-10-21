---
kind: alternate
routes:
  web: Web
steps:
  - text: Types the brand, material, color and temperatures, ticks to save the color for reuse, and binds
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product makes the spool from what was typed and adds the color to My colors in the filament library
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
        effect: changes
        facts:
          - My colors
    contexts:
      web:
        place: hub::dashboard::spools
---

# Type a filament the library lacks

## Trigger

A niche filament is not in the catalog.

## Outcome

The spool is bound, and next time the color is a search pick, not typing.
