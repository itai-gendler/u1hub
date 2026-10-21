---
kind: primary
routes:
  web: Web
steps:
  - text: Presses release on a job attached to a printer
    kind: actor
    actor: farm-operator
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
  - text: The Product detaches the job from the printer and queues it again
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: changes
        from: Printing
        to: Queued
        facts:
          - Printing on
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Undo a wrong claim

## Trigger

A printer was re-addressed or swapped and a job claims the wrong one.

## Outcome

The job is free to be claimed by the printer really printing it.

## Edge cases

- A job with nothing left to print finishes instead.
