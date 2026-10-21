---
kind: validation
routes:
  web: Web
steps:
  - text: Scans a spool's QR label
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The label names a spool this Hub does not have
    kind: condition
    entities:
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product says the label may be from another Hub or a forgotten spool
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
---

# A label this Hub does not know

## Trigger

An old label, or a label from another farm.

## Outcome

Nothing is opened or bound.
