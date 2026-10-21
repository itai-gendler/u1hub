---
kind: primary
routes:
  web: Web
steps:
  - text: Presses On on a card with a smart plug
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
  - text: The Product switches the plug on and reads it back, with live watts for a Shelly plug
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: changes
        facts:
          - Plug power
    contexts:
      web:
        place: hub::dashboard::dash
---

# Wake a printer from its card

## Trigger

A printer was off for the night.

## Outcome

The plug is on and the card comes back as the printer boots.
