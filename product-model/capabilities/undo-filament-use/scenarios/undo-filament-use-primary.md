---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Undo on a finished print's line
    kind: actor
    actor: farm-operator
    entities:
      - entity: filament-use
        effect: reads
        facts:
          - Printer
          - File
          - Grams per roll
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product adds exactly the grams it took back onto each roll and marks the line undone
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: changes
        facts:
          - Grams left
      - entity: filament-use
        effect: changes
        from: Deducted
        to: Undone
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
---

# Put the grams back

## Trigger

The wrong roll was recorded in a head, or the print did not really use its grams.

## Outcome

The rolls have their grams back; the line stays in the list, marked undone.
