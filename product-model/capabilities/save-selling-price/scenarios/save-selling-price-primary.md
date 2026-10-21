---
kind: primary
routes:
  web: Web
steps:
  - text: With a file selected, types what a piece sells for and presses Save
    kind: actor
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
          - Grams
          - Estimated time
          - Pieces per plate
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product works out what the plate brings in, per printer hour, per gram and the margin over filament at the farm's rates
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Grams
          - Estimated time
          - Pieces per plate
      - entity: hub-settings
        effect: reads
        facts:
          - Sell floor per gram
          - Filament cost per gram
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: It keeps the numbers for the file
    kind: product
    actor: farm-operator
    entities:
      - entity: selling-price
        effect: creates
        facts:
          - File
          - Price per piece
          - Pieces
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

# Price a file

## Trigger

The operator knows what this print sells for.

## Outcome

The real numbers show under the file, and the file appears in What sells.
