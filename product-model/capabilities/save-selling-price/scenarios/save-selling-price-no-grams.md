---
kind: validation
routes:
  web: Web
steps:
  - text: With a file selected, types a price and presses Save
    kind: actor
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The file carries no filament total
    kind: condition
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Grams
    contexts:
      web:
        place: hub::dashboard::dash
  - text: 'The Product refuses: there is nothing to price against'
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dash
---

# A file with no filament total

## Trigger

The slicer wrote no grams into the file.

## Outcome

Nothing is saved.
