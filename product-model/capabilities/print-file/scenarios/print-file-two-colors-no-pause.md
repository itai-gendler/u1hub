---
kind: validation
routes:
  web: Web
steps:
  - text: Maps two different colors to the same head and presses Print
    kind: actor
    actor: farm-operator
    entities:
      - entity: head
        effect: reads
        facts:
          - Number
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The file has no filament-change pause
    kind: condition
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Colors needed
    contexts:
      web:
        place: hub::dashboard::dash
  - text: 'The Product refuses: one head prints one color, so each needs its own head, or the gcode needs a pause at the swap'
    kind: product
    actor: farm-operator
    entities:
      - entity: head
        effect: reads
        facts:
          - Number
    contexts:
      web:
        place: hub::dashboard::dash
---

# Refuse two colors on one head without a pause

## Trigger

A mapping would print two colors from one roll.

## Outcome

Nothing is sent, because the print would come out in the wrong color.
