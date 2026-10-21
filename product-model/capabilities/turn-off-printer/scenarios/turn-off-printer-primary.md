---
kind: primary
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
  - text: The Product asks the printer live whether it is printing
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
  - text: It switches the plug off and reads it back
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

# Power down an idle printer

## Trigger

The farm is done for the day.

## Outcome

The printer is off.
