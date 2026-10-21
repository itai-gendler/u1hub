---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses forget on a loaded spool and confirms
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
  - text: The Product removes the spool and its record in the head, since a forgotten spool cannot stay loaded
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: removes
        from: Loaded
      - entity: head
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
---

# Forget a roll that is still loaded

## Trigger

A roll ran out in the printer.

## Outcome

The head shows no spool recorded.
