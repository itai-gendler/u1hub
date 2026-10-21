---
kind: primary
result: achieved
routes:
  web: Web
steps:
  - text: Holds a new roll's tag to the phone on the Spools tab
    kind: actor
    capability: look-up-spool
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product finds no spool with that tag and opens the bind panel with the tag filled in
    kind: product
    capability: look-up-spool
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Tags
    contexts:
      web:
        place: hub::dashboard::spools
  - text: Searches the filament library, picks the match and presses Bind this spool
    kind: actor
    capability: bind-spool
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
  - text: The Product makes the spool with the tag attached
    kind: product
    capability: bind-spool
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
    contexts:
      web:
        place: hub::dashboard::spools
---

# From an unknown tag to a bound spool

## Trigger

A new tagged roll arrives.

## Outcome

The roll is on the shelf, ready to load into a head from its card.
