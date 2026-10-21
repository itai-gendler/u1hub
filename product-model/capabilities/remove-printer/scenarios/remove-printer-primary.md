---
kind: primary
routes:
  web: Web
steps:
  - text: Removes a printer's row and presses Save
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::printers
  - text: The Product drops the printer; a Dispatch copy it held goes back to the queue with a note
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: removes
        from: In service
      - entity: job
        effect: changes
        from: Printing
        to: Queued
        facts:
          - Printing on
          - Notice
    contexts:
      web:
        place: hub::dashboard::printers
---

# Retire a printer

## Trigger

A printer was sold.

## Outcome

Its card and lane are gone; nothing planned is left waiting on it.
