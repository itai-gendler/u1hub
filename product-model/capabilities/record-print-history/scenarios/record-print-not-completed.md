---
kind: edge
routes:
  web: Web
steps:
  - text: A print the Hub saw start is cancelled or fails
    kind: condition
    unattended: true
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product remembers nothing for it
    kind: product
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
---

# A print stops without completing

## Trigger

A print is cancelled or errors.

## Outcome

A failed print teaches nothing; the last good loadout stays.
