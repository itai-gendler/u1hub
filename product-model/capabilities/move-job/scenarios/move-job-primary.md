---
kind: primary
routes:
  web: Web
steps:
  - text: Taps a planned block, picks a printer under Move and presses Move
    kind: actor
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - File
          - Pinned printer
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product pins the job to that printer and replans
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: changes
        facts:
          - Pinned printer
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Put a job on a chosen printer

## Trigger

The operator wants a job on the printer by the door.

## Outcome

Every copy of the job is planned on that printer.

## Edge cases

- A pin to a printer taken down for maintenance falls back to the other printers and is honored again when it returns.
