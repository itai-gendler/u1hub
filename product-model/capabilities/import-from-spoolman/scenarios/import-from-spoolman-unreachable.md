---
kind: edge
routes:
  web: Web
steps:
  - text: Presses Import on the Spoolman card
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: Spoolman does not answer within eight seconds or answers with an error
    kind: condition
    entities:
      - entity: spoolman-connection
        effect: reads
        facts:
          - Spoolman address
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product says the import failed and why, and notes it
    kind: product
    actor: farm-operator
    entities:
      - entity: spoolman-connection
        effect: changes
        facts:
          - Last import
    contexts:
      web:
        place: hub::dashboard::spools
---

# Spoolman does not answer

## Trigger

The Spoolman server is down or the address is wrong.

## Outcome

No spool changes.
