---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Pause on a printing card
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
          - Print state
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product asks the printer to pause and holds a spinner on the button, ignoring a second tap, until the printer answers
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

# Pause from the card

## Trigger

Something on the bed needs a look.

## Outcome

The card reads Paused once the printer reports it; a printer that does not answer is named on the card.

## Edge cases

- A slow printer is never sent the same command twice.
