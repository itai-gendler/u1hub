---
kind: alternate
routes:
  web: Web
steps:
  - text: A printer finishes a print, and a roll it used was imported from Spoolman with write-back on
    kind: condition
    unattended: true
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
      - entity: spoolman-connection
        effect: reads
        facts:
          - Write-back
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product takes the grams off the roll on the Hub
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
          - Spoolman status
    contexts:
      web:
        place: hub::dashboard::spools
  - text: It records the same grams as used in Spoolman, as an amount used and never as a weight; while Spoolman cannot be reached they wait and are retried every ten minutes
    kind: product
    entities:
      - entity: filament-use
        effect: changes
        facts:
          - Spoolman status
      - entity: spoolman-connection
        effect: reads
        facts:
          - Spoolman address
    contexts:
      web:
        place: hub::dashboard::spools
---

# Record the grams in Spoolman too

## Trigger

Spoolman is the farm's master list.

## Outcome

Spoolman's remaining weight drops by what the print used; nothing else about the roll is ever changed there.
