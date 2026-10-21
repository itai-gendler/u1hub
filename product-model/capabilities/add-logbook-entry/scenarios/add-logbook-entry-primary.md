---
kind: primary
routes:
  web: Web
steps:
  - text: Presses + Add entry, picks a printer and Issue, Maintenance or Note, writes what happened and, if known, what fixed it, and saves
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
  - text: The Product logs the entry with the printer's print hours at the time
    kind: product
    actor: farm-operator
    entities:
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
        facts:
          - Print hours
    contexts:
      web:
        place: hub::dashboard::logbook
---

# Log an issue and its fix

## Trigger

Something happened worth remembering.

## Outcome

The entry is in the log; an issue with no fix shows as still open.
