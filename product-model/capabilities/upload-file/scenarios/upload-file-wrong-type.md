---
kind: validation
routes:
  web: Web
steps:
  - text: With a file selected, presses Upload on a printer's card
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The printer belongs to a different printer type than the file's folder
    kind: condition
    entities:
      - entity: printer
        effect: reads
        facts: []
      - entity: printer-type
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product refuses and says to switch to that type
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
---

# Refuse a printer of another type

## Trigger

A stale page or a hand-made request aims a file at the wrong kind of machine.

## Outcome

Nothing is sent; a U1 file never reaches another type's printer, or the reverse.
