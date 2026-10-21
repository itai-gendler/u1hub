---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Resume on a paused job
    kind: actor
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product queues the job and replans
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: changes
        from: Paused
        to: Queued
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Let a job be planned again

## Trigger

The hold is over.

## Outcome

The job's copies are back on the timeline.
