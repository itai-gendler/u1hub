---
kind: alternate
routes:
  web: Web
steps:
  - text: A task's print hours or days run out on a printer
    kind: condition
    unattended: true
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print hours
      - entity: upkeep-task
        effect: reads
        facts:
          - Last done
          - Every print hours
          - Every days
    contexts:
      web:
        place: hub::dashboard::logbook
  - text: The Product marks the task due for that printer, on its card and in the schedule
    kind: product
    entities:
      - entity: upkeep-task
        effect: changes
        facts:
          - Due
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::logbook
---

# A task runs out of hours or days

## Trigger

Whichever interval runs out first.

## Outcome

The printer's card shows the task due; at 85 percent of the interval it shows as coming up.
