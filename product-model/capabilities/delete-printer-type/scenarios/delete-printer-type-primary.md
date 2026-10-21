---
kind: primary
routes:
  web: Web
steps:
  - text: Presses delete on a type and confirms
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer-type
        effect: reads
        facts:
          - Name
          - Printers
    contexts:
      web:
        place: hub::dashboard::printers
  - text: The Product removes the type and its Up next entries; its folder and files are kept
    kind: product
    actor: farm-operator
    entities:
      - entity: printer-type
        effect: removes
      - entity: queue-entry
        effect: removes
    contexts:
      web:
        place: hub::dashboard::printers
---

# Delete an empty type

## Trigger

The last printer of that kind left the farm.

## Outcome

The type's tab is gone; its gcode is still on disk.
