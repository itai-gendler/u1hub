---
kind: primary
routes:
  web: Web
steps:
  - text: Presses + Add manually, fills in the name, address, type and plug, and presses Save
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer-type
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::printers
  - text: The Product adds the printer to its type and connects to it for live status
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: creates
        to: In service
        facts:
          - Name
          - Address
          - Smart plug
      - entity: printer-type
        effect: reads
        facts:
          - Printers
    contexts:
      web:
        place: hub::dashboard::printers
---

# Add a machine to the farm

## Trigger

A new printer arrived.

## Outcome

Its card is on the Dash and its lane on Dispatch.
