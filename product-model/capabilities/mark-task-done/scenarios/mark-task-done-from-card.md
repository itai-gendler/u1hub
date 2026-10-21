---
kind: alternate
routes:
  web: Web
steps:
  - text: Taps the due line on a printer's card
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
        place: hub::dashboard::dash
  - text: The Product opens the Logbook on that printer
    kind: product
    actor: farm-operator
    entities:
      - entity: upkeep-task
        effect: reads
        facts:
          - Task
          - Due
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::logbook
  - text: Presses Done, adds a note and presses Mark done
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
  - text: It restarts the task's clock on that printer and writes the maintenance into the log
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

# Start from the printer's card

## Trigger

The card said a task is due.

## Outcome

The card's due line clears.
