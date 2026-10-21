---
kind: edge
routes:
  web: Web
steps:
  - text: Taps a head's color on an idle printer and picks a color
    kind: actor
    actor: farm-operator
    entities:
      - entity: head
        effect: reads
        facts:
          - Number
          - Loaded color
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The head has no material, or the printer does not take the one picked
    kind: condition
    entities:
      - entity: head
        effect: reads
        facts:
          - Material
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product sets the color and warns that the printer resets it to white the next time it reads the spool until a material is set
    kind: product
    actor: farm-operator
    entities:
      - entity: head
        effect: changes
        facts:
          - Loaded color
      - entity: printer
        effect: reads
        facts: []
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
---

# A color without a material the printer takes

## Trigger

A material the printer does not know is picked.

## Outcome

The color is set for now, and the operator knows to set the material on the touchscreen.
