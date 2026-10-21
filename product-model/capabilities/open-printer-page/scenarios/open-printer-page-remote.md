---
kind: alternate
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
  - text: The browser reached the Hub from outside its network
    kind: condition
    entities: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product opens the printer's page through the Hub, behind the Hub's own sign-in
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

# Open the printer through the Hub from away

## Trigger

The operator is away from home.

## Outcome

The printer's page opens without the printer being put on the internet itself; how well it works can depend on the network setup.
