---
kind: primary
routes:
  web: Web
steps:
  - text: Taps a planned block and presses Push back one
    kind: actor
    actor: farm-operator
    entities:
      - entity: job
        as: pushed
        effect: reads
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product records that the job waits for the job planned after it, and replans so it starts only once that one finishes
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: changes
        facts:
          - Pushed back behind
        as: pushed
      - entity: job
        as: next
        effect: reads
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Let the next job go first

## Trigger

Three jobs want the one green roll at the same time.

## Outcome

The job runs after the next one; pressing again pushes it one more place.

## Edge cases

- When the job it waits for leaves the list, it goes back to its normal turn.
