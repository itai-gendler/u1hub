---
kind: alternate
routes:
  web: Web
steps:
  - text: Clears a typed runtime
    kind: actor
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - Runtime
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product goes back to the learned time, or the slicer's estimate
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: changes
        facts:
          - Runtime
      - entity: library-file
        effect: reads
        facts:
          - Run times
          - Estimated time
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Go back to the file's own figure

## Trigger

The typed time is no longer right.

## Outcome

The block's panel says again where the runtime came from.
