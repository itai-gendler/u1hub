---
kind: primary
routes:
  web: Web
steps:
  - text: Types the Spoolman address, ticks write-back if wanted, and saves
    kind: actor
    actor: farm-operator
    entities:
      - entity: spoolman-connection
        effect: reads
        facts:
          - Spoolman address
          - Write-back
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product keeps the address, accepting it with or without a pasted /api/v1, and the write-back choice
    kind: product
    actor: farm-operator
    entities:
      - entity: spoolman-connection
        effect: changes
        facts:
          - Spoolman address
          - Write-back
    contexts:
      web:
        place: hub::dashboard::spools
---

# Point the Hub at Spoolman

## Trigger

Spoolman is being connected for the first time, or Spoolman should stay the master list.

## Outcome

Import uses the address; with write-back on, the grams each print uses are recorded in Spoolman too.
