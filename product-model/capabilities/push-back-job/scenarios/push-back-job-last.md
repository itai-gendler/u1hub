---
kind: validation
routes:
  web: Web
steps:
  - text: Presses Push back one on a job
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
  - text: The job is already last in the plan, or has no place in it
    kind: condition
    entities:
      - entity: job
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product refuses and says why
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Nothing to push behind

## Trigger

There is no job after it.

## Outcome

The plan is unchanged.
