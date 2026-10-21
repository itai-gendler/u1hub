---
kind: alternate
routes:
  web: Web
steps:
  - text: Lowers a job's count to the copies already printed
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
  - text: No copy of it is on a printer
    kind: condition
    entities:
      - entity: job
        effect: reads
        facts:
          - Printing on
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product finishes the job, the same way as its last copy finishing
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: removes
        from: Queued
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Lower the count to what is printed

## Trigger

The customer needs fewer.

## Outcome

The job leaves the list.
