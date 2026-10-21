---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses Undo on a line whose grams were recorded in Spoolman
    kind: actor
    actor: farm-operator
    entities:
      - entity: filament-use
        effect: reads
        facts:
          - Spoolman status
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product puts the grams back on the Hub's rolls and marks the line undone
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
        facts:
          - Spoolman status
    contexts:
      web:
        place: hub::dashboard::spools
  - text: It takes the same grams back out of Spoolman, even if write-back has been turned off since, retrying while Spoolman cannot be reached
    kind: product
    actor: farm-operator
    entities:
      - entity: spoolman-connection
        effect: reads
        facts:
          - Spoolman address
    contexts:
      web:
        place: hub::dashboard::spools
---

# Undo grams that reached Spoolman

## Trigger

A deduction that write-back already sent was wrong.

## Outcome

The Hub and Spoolman agree again.
