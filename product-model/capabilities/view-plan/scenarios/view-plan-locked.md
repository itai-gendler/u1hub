---
kind: alternate
routes:
  web: Web
steps:
  - text: Opens Dispatch
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The plan is locked
    kind: condition
    entities:
      - entity: dispatch-settings
        effect: reads
        facts:
          - Locked plan
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product shows the locked times, dropping copies that ran or were removed, and lists work added since the lock instead of placing it
    kind: product
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: reads
        facts:
          - Locked plan
      - entity: job
        effect: reads
        facts:
          - Remaining
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# A locked plan holds still

## Trigger

The operator approved a plan and wants it to stop moving.

## Outcome

The board is still; running prints and printer states stay live.
