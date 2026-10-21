---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Download diagnostics
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::settings
  - text: >-
      The Product writes one file: the Hub's version, the printer types and each printer's detected capabilities, the recent Hub log, and the tail of each printer's klippy and moonraker logs, with
      addresses and tokens scrubbed
    kind: product
    actor: farm-operator
    entities:
      - entity: printer-type
        effect: reads
        facts:
          - Name
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::settings
---

# Make a file for a bug report

## Trigger

A non-U1 printer misbehaves, or something else went wrong.

## Outcome

The file is saved for the operator to review and attach to a GitHub issue; nothing is sent automatically.
