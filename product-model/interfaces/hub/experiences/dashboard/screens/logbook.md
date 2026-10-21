---
entities:
  - entity: logbook-entry
    shows:
      - Printer name
      - Kind
      - What happened
      - Fix
      - When
      - Print hours
      - Source
      - File
      - Back in service
    collects:
      - Kind
      - What happened
      - Fix
  - entity: upkeep-task
    shows:
      - Task
      - Printers
      - Every print hours
      - Every days
      - Notes
      - Last done
      - Due
    collects:
      - Task
      - Printers
      - Every print hours
      - Every days
      - Notes
  - entity: printer
    shows:
      - Name
      - Print hours
references:
  - kind: code
    role: implementation
    target: public/modules/logbook-ui.js
---

# Logbook

The log of what happened to each printer and what fixed it, and the schedule of upkeep that comes round again.
