---
kind: validation
routes:
  web: Web
steps:
  - text: Presses delete on a type
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
  - text: Printers still belong to it, or it is the built-in U1 type
    kind: condition
    entities:
      - entity: printer-type
        effect: reads
        facts:
          - Printers
          - Built-in
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::printers
  - text: The Product refuses and says to move or remove those printers first
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::printers
---

# A type still in use, or the U1 type

## Trigger

The type still has machines.

## Outcome

The type stays.
