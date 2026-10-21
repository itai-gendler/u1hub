---
kind: alternate
routes:
  web: Web
steps:
  - text: Ticks Auto-start on every card under Chamber cameras in Settings, on this device
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::settings
  - text: The Product starts each card's camera as it comes into view
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

# Every card starts its camera on this device

## Trigger

A wall screen in the shop should show every chamber.

## Outcome

Cameras run on that device only; other devices still start them by hand.
