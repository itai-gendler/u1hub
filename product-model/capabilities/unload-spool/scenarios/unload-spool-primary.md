---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Unload on a loaded spool
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Color name
          - Loaded in
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product clears the spool's record in the head
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: changes
        from: Loaded
        to: On the shelf
        facts:
          - Loaded in
      - entity: head
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
---

# Take a roll off a printer

## Trigger

A roll came off a printer.

## Outcome

The spool is on the shelf and the head shows none recorded.
