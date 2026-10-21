---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Live view on a card
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
  - text: The Product shows a frame from the printer's chamber camera about once a second, larger on a tap
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: When nobody has watched for a minute, the Product stops asking the printer for frames
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
---

# Look inside one printer

## Trigger

The operator wants to see the print without walking over.

## Outcome

The print is on screen; closing the view stops the stream.
