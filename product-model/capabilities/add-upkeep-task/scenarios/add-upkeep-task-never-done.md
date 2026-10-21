---
kind: alternate
routes:
  web: Web
steps:
  - text: Adds a task with never done yet ticked
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::logbook
  - text: The Product adds the task as due now on every printer it covers
    kind: product
    actor: farm-operator
    entities:
      - entity: upkeep-task
        effect: creates
        facts:
          - Task
          - Printers
          - Every print hours
          - Every days
          - Notes
          - Due
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::logbook
---

# Schedule upkeep that has never been done

## Trigger

The upkeep is overdue already.

## Outcome

The printer cards show it due.
