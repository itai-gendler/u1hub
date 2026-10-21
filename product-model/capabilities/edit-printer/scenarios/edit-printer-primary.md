---
kind: primary
routes:
  web: Web
steps:
  - text: Changes a printer's name, address, type or plug and presses Save
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
          - Address
          - Smart plug
    contexts:
      web:
        place: hub::dashboard::printers
  - text: The Product saves the printer under the same identity and reconnects
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: changes
        facts:
          - Name
          - Address
          - Smart plug
    contexts:
      web:
        place: hub::dashboard::printers
---

# Rename or re-address a printer

## Trigger

A printer was moved to a new address.

## Outcome

Dispatch claims, maintenance and pins stay with the machine, even when the list is reordered.
