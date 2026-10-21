---
kind: alternate
routes:
  web: Web
steps:
  - text: With a priced file selected, types a new price and presses Save
    kind: actor
    actor: farm-operator
    entities:
      - entity: selling-price
        effect: reads
        facts:
          - Price per piece
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product replaces the file's numbers with the new ones
    kind: product
    actor: farm-operator
    entities:
      - entity: selling-price
        effect: changes
        facts:
          - Price per piece
          - Revenue
          - Per printer hour
          - Per gram
          - Margin
          - Below floor
          - Saved
    contexts:
      web:
        place: hub::dashboard::dash
---

# Price a file again

## Trigger

The price changed.

## Outcome

The latest price wins; the table is never recomputed from files that changed since.
