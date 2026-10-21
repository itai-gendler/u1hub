---
kind: alternate
routes:
  web: Web
steps:
  - text: Selects a library file in the list
    kind: actor
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::files
  - text: The same file content finished printing before with spools recorded in its heads
    kind: condition
    entities:
      - entity: filament-memory
        effect: reads
        facts:
          - Printed
          - Spools used
      - entity: spool
        effect: reads
        facts: []
      - entity: head
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product shows which spool was in each head last time, greying out a spool forgotten since, so the same heads can be chosen again
    kind: product
    actor: farm-operator
    entities:
      - entity: filament-memory
        effect: reads
        facts:
          - Printed
          - Spools used
      - entity: spool
        effect: reads
        facts:
          - Color name
          - Color
          - Brand
      - entity: head
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
---

# Recall the spools a file printed with

## Trigger

A file the farm printed before is selected again.

## Outcome

Last time's loadout is one tap from being the mapping again, even when the file was renamed or moved since.
