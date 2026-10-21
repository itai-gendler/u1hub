---
kind: primary
routes:
  web: Web
steps:
  - text: Presses the lock above the timeline
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
  - text: The Product computes a fresh live plan and freezes its placed copies
    kind: product
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: changes
        from: Fluid
        to: Locked
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

# Lock what is on screen

## Trigger

The plan is right and should hold.

## Outcome

The times stay where they are until unlocked.
