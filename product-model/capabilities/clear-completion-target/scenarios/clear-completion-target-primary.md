---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Clear beside the target
    kind: actor
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: reads
        facts:
          - Completion target
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product drops the target and replans
    kind: product
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: changes
        facts:
          - Completion target
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Drop the target

## Trigger

The show is over.

## Outcome

Only jobs with deadlines of their own are judged.
