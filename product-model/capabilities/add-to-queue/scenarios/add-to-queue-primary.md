---
kind: primary
routes:
  web: Web
steps:
  - text: With a file selected, presses Add to queue
    kind: actor
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product puts the file at the end of Up next, kept across Hub restarts
    kind: product
    actor: farm-operator
    entities:
      - entity: queue-entry
        effect: creates
        facts:
          - File
          - Added
          - Position
    contexts:
      web:
        place: hub::dashboard::files
---

# Line a file up for later

## Trigger

The operator wants to print a file when a machine frees up.

## Outcome

The file is last on Up next for everyone using the Hub, on any device.
