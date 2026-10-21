---
kind: primary
routes:
  web: Web
steps:
  - text: Clicks a printer's name on its card
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
  - text: The browser is on the Hub's own network
    kind: condition
    entities: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product opens the printer's own page at its address, so its live data and controls work as they do on the printer
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Address
    contexts:
      web:
        place: hub::dashboard::dash
---

# Open the printer directly on the network

## Trigger

Something needs the printer's full interface.

## Outcome

Fluidd for that printer is open in a new tab.
