---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Done on a due task for a printer, adds an optional note and presses Mark done
    kind: actor
    actor: farm-operator
    entities:
      - entity: upkeep-task
        effect: reads
        facts:
          - Task
          - Due
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::logbook
  - text: The Product asks every printer for its print hours now
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print hours
    contexts:
      web:
        place: hub::dashboard::logbook
  - text: It restarts the task's clock on that printer and writes a maintenance entry with the note and the print hours
    kind: product
    actor: farm-operator
    entities:
      - entity: upkeep-task
        effect: changes
        facts:
          - Last done
          - Due
      - entity: logbook-entry
        effect: creates
        facts:
          - Printer name
          - Kind
          - What happened
          - Fix
          - When
          - Print hours
          - Source
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::logbook
---

# Record upkeep as done

## Trigger

The rods were lubricated.

## Outcome

The task is OK again on that printer, and the log shows when it was done.
