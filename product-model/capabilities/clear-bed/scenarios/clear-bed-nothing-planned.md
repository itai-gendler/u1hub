---
kind: edge
routes:
  web: Web
steps:
  - text: Presses Bed cleared → next on a printer's lane
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: No copy is planned for that printer
    kind: condition
    entities:
      - entity: job
        effect: reads
        facts: []
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product says nothing is planned
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Nothing is planned next

## Trigger

The queue is empty for that printer.

## Outcome

The bed is marked clear and the printer waits.
