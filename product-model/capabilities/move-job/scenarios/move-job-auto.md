---
kind: alternate
routes:
  web: Web
steps:
  - text: Picks automatic under Move and presses Move
    kind: actor
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - Pinned printer
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product drops the pin and where its copies sat, and replans
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: changes
        facts:
          - Pinned printer
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Let the planner choose again

## Trigger

The pin is no longer wanted.

## Outcome

The job goes wherever it finishes soonest.
