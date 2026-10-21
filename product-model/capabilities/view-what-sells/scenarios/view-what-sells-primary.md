---
kind: primary
routes:
  web: Web
steps:
  - text: Opens the table from the worth-printing line
    kind: actor
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product lists every priced file of the selected type with its numbers and totals, sorted by money per printer hour
    kind: product
    actor: farm-operator
    entities:
      - entity: selling-price
        effect: reads
        facts:
          - File
          - Price per piece
          - Revenue
          - Per printer hour
          - Per gram
          - Margin
          - Below floor
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::what-sells
  - text: Sorts by another column
    kind: actor
    actor: farm-operator
    entities:
      - entity: selling-price
        effect: reads
        facts:
          - Per gram
    contexts:
      web:
        place: hub::dashboard::what-sells
  - text: The Product reorders the table
    kind: product
    actor: farm-operator
    entities:
      - entity: selling-price
        effect: reads
        facts:
          - Per gram
          - Margin
          - Revenue
    contexts:
      web:
        place: hub::dashboard::what-sells
---

# Compare priced files

## Trigger

The operator decides what to print more of.

## Outcome

The most and least profitable files are at the two ends of the table; files under the sell floor are marked.

## Edge cases

- The Hub never decides anything from these numbers; Dispatch does not read them.
