---
kind: validation
routes:
  web: Web
steps:
  - text: Presses Off on a card with a smart plug
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
          - Plug power
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The printer is printing or paused, or does not answer whether it is
    kind: condition
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product refuses and leaves the plug on
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Plug power
    contexts:
      web:
        place: hub::dashboard::dash
---

# Refuse to cut power mid-print

## Trigger

Off is pressed on the wrong card, or while the printer cannot be reached.

## Outcome

The print keeps running; when the state cannot be confirmed the Hub fails safe and leaves the power on.
