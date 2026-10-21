---
kind: primary
routes:
  web: Web
steps:
  - text: Presses the remove mark on a task and Remove task
    kind: actor
    actor: farm-operator
    entities:
      - entity: upkeep-task
        effect: reads
        facts:
          - Task
    contexts:
      web:
        place: hub::dashboard::logbook
  - text: The Product removes the task; the maintenance it wrote into the log stays
    kind: product
    actor: farm-operator
    entities:
      - entity: upkeep-task
        effect: removes
    contexts:
      web:
        place: hub::dashboard::logbook
---

# Drop a task

## Trigger

The upkeep no longer applies.

## Outcome

The task is off the schedule and off the printer cards.
