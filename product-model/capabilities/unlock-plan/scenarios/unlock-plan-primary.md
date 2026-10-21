---
kind: primary
routes:
  web: Web
steps:
  - text: Presses the lock above a locked timeline
    kind: actor
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: reads
        facts:
          - Locked plan
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product drops the frozen plan and replans live
    kind: product
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: changes
        from: Locked
        to: Fluid
        facts:
          - Locked plan
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Let the plan move again

## Trigger

The day changed too much for the locked plan.

## Outcome

The timeline follows the farm again.
