---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Resume on a paused card
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
          - Print state
          - Pause reason
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product asks the printer to resume and holds a spinner on the button until the printer answers
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
    contexts:
      web:
        place: hub::dashboard::dash
---

# Resume from the card

## Trigger

Whatever paused the print is sorted out.

## Outcome

The card reads Printing again once the printer reports it.
