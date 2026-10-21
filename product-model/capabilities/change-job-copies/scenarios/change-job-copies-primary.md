---
kind: primary
routes:
  web: Web
steps:
  - text: Presses plus or minus on a job's count
    kind: actor
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - Copies
          - Remaining
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product changes the copies and the copies still to print by the same amount and replans
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: changes
        facts:
          - Copies
          - Remaining
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Print one more

## Trigger

The order changed.

## Outcome

The timeline shows the new number of copies.
