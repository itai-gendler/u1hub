---
kind: primary
routes:
  web: Web
steps:
  - text: Presses + Add task, names it, picks a printer or all, sets print hours, days or both, and saves
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::logbook
  - text: The Product adds the task and starts its clock now on every printer it covers, at each printer's current print hours
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
          - Last done
      - entity: printer
        effect: reads
        facts:
          - Print hours
    contexts:
      web:
        place: hub::dashboard::logbook
---

# Schedule upkeep that counts from today

## Trigger

Rods need lubricating every 200 print hours.

## Outcome

The task is on the schedule; a printer with two thousand hours is not instantly overdue.
