---
kind: primary
routes:
  web: Web
steps:
  - text: Presses the remove mark on a job
    kind: actor
    actor: farm-operator
    entities:
      - entity: job
        as: removed
        effect: reads
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product removes the job, and jobs pushed back behind it go back to their normal turn
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: removes
        from: Queued
        as: removed
      - entity: job
        effect: changes
        facts:
          - Pushed back behind
        as: waiting
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Drop a job

## Trigger

The order was cancelled.

## Outcome

The job is gone from the list and the timeline; its file stays in the library.

## Edge cases

- A bundle left with no jobs goes too.
