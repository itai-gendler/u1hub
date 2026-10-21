---
kind: primary
routes:
  web: Web
steps:
  - text: A printer pauses or errors with a reason in the firmware's own words, such as a tangle, a runout or a heater fault
    kind: condition
    unattended: true
    entities:
      - entity: printer
        effect: reads
        facts:
          - Pause reason
          - Printing file
    contexts:
      web:
        place: hub::dashboard::logbook
  - text: The Product logs an issue with the reason, the file and the print hours, waiting for its fix
    kind: product
    entities:
      - entity: logbook-entry
        effect: creates
        facts:
          - Printer name
          - Kind
          - What happened
          - When
          - Print hours
          - Source
          - File
    contexts:
      web:
        place: hub::dashboard::logbook
---

# A printer pauses with a reason

## Trigger

The firmware stops a print and says why.

## Outcome

The issue is in the log without anyone typing it.

## Edge cases

- The same reason on the same printer within half an hour is one entry.
- A manual pause or a filament-change pause carries no reason and is not logged.
