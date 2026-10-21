---
kind: primary
routes:
  web: Web
steps:
  - text: Taps a head's color on an idle printer and picks a color and a material
    kind: actor
    actor: farm-operator
    entities:
      - entity: head
        effect: reads
        facts:
          - Number
          - Loaded color
          - Material
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product checks live that the printer is idle and the head is loaded and editable
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
      - entity: head
        effect: reads
        facts:
          - Loaded
          - Official spool
    contexts:
      web:
        place: hub::dashboard::dash
  - text: It sets the material and the color on the printer, then reads them back before showing success
    kind: product
    actor: farm-operator
    entities:
      - entity: head
        effect: changes
        facts:
          - Loaded color
          - Material
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
---

# Set a head's color and material

## Trigger

A roll was loaded at the printer without its color being set.

## Outcome

The head shows the new color and material on the card and on the touchscreen, and matching uses it.
