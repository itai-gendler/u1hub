---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Update filament library
    kind: actor
    actor: farm-operator
    entities:
      - entity: filament-library
        effect: reads
        facts:
          - Swatches
          - Last updated
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product pulls the whole catalog from FilamentColors.xyz and keeps it beside the Hub's settings, in place of the shipped copy
    kind: product
    actor: farm-operator
    entities:
      - entity: filament-library
        effect: changes
        facts:
          - Swatches
          - Last updated
    contexts:
      web:
        place: hub::dashboard::spools
---

# Refresh the catalog

## Trigger

New filaments are in the catalog.

## Outcome

Searches when binding a spool see the new swatches.
