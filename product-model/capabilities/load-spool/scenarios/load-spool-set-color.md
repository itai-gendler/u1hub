---
kind: alternate
routes:
  web: Web
steps:
  - text: Picks a head on an idle U1, leaves also set that head's color on the printer ticked, and presses Load here
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Color name
          - Color
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
        place: hub::dashboard::spools
  - text: The Product records the spool in that head
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: changes
        from: On the shelf
        to: Loaded
        facts:
          - Loaded in
      - entity: head
        effect: reads
        facts:
          - Number
    contexts:
      web:
        place: hub::dashboard::spools
  - text: It sets the head's color and material on the printer from the spool
    kind: product
    actor: farm-operator
    entities:
      - entity: head
        effect: changes
        facts:
          - Loaded color
          - Material
      - entity: spool
        effect: reads
        facts:
          - Color
          - Material
      - entity: printer
        effect: reads
        facts:
          - Print state
    contexts:
      web:
        place: hub::dashboard::spools
---

# Load and set the head's color

## Trigger

A tagless roll is mounted on a U1, whose touchscreen would otherwise show the wrong color.

## Outcome

Matching sees the head like an official RFID roll.
