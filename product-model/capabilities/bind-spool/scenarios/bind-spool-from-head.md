---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses Bind to this loaded color on a printer's head
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
      - entity: head
        effect: reads
        facts:
          - Number
          - Loaded color
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product reads that head's color and material from the printer and makes the spool from them
    kind: product
    actor: farm-operator
    entities:
      - entity: head
        effect: reads
        facts:
          - Loaded
          - Loaded color
          - Material
      - entity: printer
        effect: reads
        facts: []
      - entity: spool
        effect: creates
        to: On the shelf
        facts:
          - Brand
          - Material
          - Variant
          - Color name
          - Color
          - Hot end temperature
          - Bed temperature
          - Tags
          - Origin
    contexts:
      web:
        place: hub::dashboard::spools
---

# Take the identity from a loaded head

## Trigger

The roll is already loaded and its color is set on the printer.

## Outcome

The spool carries the head's color.

## Edge cases

- An empty head, or one with no color, is refused.
