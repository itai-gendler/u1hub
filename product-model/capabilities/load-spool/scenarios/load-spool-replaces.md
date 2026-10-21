---
kind: alternate
routes:
  web: Web
steps:
  - text: Picks a head that already has a spool recorded and presses Load here
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        as: incoming
        effect: reads
        facts:
          - Color name
      - entity: head
        effect: reads
        facts:
          - Number
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product records the new spool in the head and puts the one that was there back on the shelf, naming it
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: changes
        from: On the shelf
        to: Loaded
        facts:
          - Loaded in
        as: incoming
      - entity: spool
        effect: changes
        from: Loaded
        to: On the shelf
        facts:
          - Loaded in
        as: outgoing
      - entity: head
        effect: reads
        facts:
          - Number
    contexts:
      web:
        place: hub::dashboard::spools
---

# Load into a head that already has a roll

## Trigger

A roll was swapped at the printer.

## Outcome

The head holds the new spool and the old one is on the shelf.
