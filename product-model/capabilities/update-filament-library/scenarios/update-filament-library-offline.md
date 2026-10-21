---
kind: edge
routes:
  web: Web
steps:
  - text: Presses Update filament library
    kind: actor
    actor: farm-operator
    entities:
      - entity: filament-library
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: FilamentColors.xyz cannot be reached
    kind: condition
    entities: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product says so; the library it has keeps working offline
    kind: product
    actor: farm-operator
    entities:
      - entity: filament-library
        effect: reads
        facts:
          - Last updated
    contexts:
      web:
        place: hub::dashboard::spools
---

# The catalog cannot be reached

## Trigger

The farm network has no internet.

## Outcome

The import keeps using the address saved before.
