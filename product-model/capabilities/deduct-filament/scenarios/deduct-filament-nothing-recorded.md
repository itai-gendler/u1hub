---
kind: alternate
routes:
  web: Web
steps:
  - text: A printer finishes a print of a file that is in the Hub library
    kind: condition
    unattended: true
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
    contexts:
      web:
        place: hub::dashboard::spools
  - text: A head has no spool recorded, or its spool has no grams left recorded
    kind: condition
    entities:
      - entity: spool
        effect: reads
        facts:
          - Grams left
          - Loaded in
      - entity: head
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product skips that head and says why in the log, never inventing a number
    kind: product
    entities:
      - entity: head
        effect: reads
        facts:
          - Number
    contexts:
      web:
        place: hub::dashboard::spools
---

# Heads with nothing to deduct from

## Trigger

A roll was never weighed, or never loaded in the Hub.

## Outcome

Only rolls with real numbers change.
