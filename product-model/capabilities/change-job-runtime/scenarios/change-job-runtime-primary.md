---
kind: primary
routes:
  web: Web
steps:
  - text: Clicks a job's runtime and types the minutes per copy
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
  - text: The Product plans the job at that time from now on, ahead of the slicer and of anything learned
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: changes
        facts:
          - Runtime
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Type a copy's real time

## Trigger

The operator knows this print runs long.

## Outcome

The job's blocks on the timeline have the typed length.
