---
kind: primary
routes:
  web: Web
steps:
  - text: A printer finishes a print of a file that is in the Hub library, and automatic deduction is on
    kind: condition
    unattended: true
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
      - entity: inventory-settings
        effect: reads
        facts:
          - Deduct automatically
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product reads the grams each of the file's colors used and, through the printer's own head mapping, finds the head that printed each
    kind: product
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Colors needed
      - entity: head
        effect: reads
        facts:
          - Number
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: It takes the grams off the spool recorded in each head, never below zero, and notes what they cost at each roll's price
    kind: product
    entities:
      - entity: spool
        effect: changes
        facts:
          - Grams left
      - entity: filament-use
        effect: creates
        to: Deducted
        facts:
          - Printer
          - File
          - Finished
          - Grams per roll
          - Cost
      - entity: head
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
---

# Take a finished print's grams off its rolls

## Trigger

A print completes on a printer whose heads have spools recorded.

## Outcome

The rolls show less left and the Filament used card lists the print with its grams, its cost and an Undo.

## Edge cases

- A cancelled or failed print deducts nothing.
- A roll that reaches zero is marked empty, not hidden.
