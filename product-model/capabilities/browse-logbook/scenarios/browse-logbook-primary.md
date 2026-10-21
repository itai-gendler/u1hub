---
kind: primary
routes:
  web: Web
steps:
  - text: Opens Logbook, picks a printer or a kind and searches what and fix, such as clog
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
  - text: The Product lists the matching entries newest first, each with its printer, date, print hours at the time, source and fix
    kind: product
    actor: farm-operator
    entities:
      - entity: logbook-entry
        effect: reads
        facts:
          - Printer name
          - Kind
          - What happened
          - Fix
          - When
          - Print hours
          - Source
          - File
          - Back in service
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::logbook
---

# Search for how it was fixed last time

## Trigger

A nozzle clogged again.

## Outcome

What worked before is on screen; an outage shows how long the printer was out.
