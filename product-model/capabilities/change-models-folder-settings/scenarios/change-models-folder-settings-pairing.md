---
kind: alternate
routes:
  web: Web
steps:
  - text: Opens Folder and presses Copy token
    kind: actor
    actor: farm-operator
    entities:
      - entity: models-settings
        effect: reads
        facts:
          - Pairing token
    contexts:
      web:
        place: hub::dashboard::models
  - text: The Product copies the Hub's address and token to paste into 3MF Explorer's settings
    kind: product
    actor: farm-operator
    entities:
      - entity: models-settings
        effect: reads
        facts:
          - Pairing token
      - entity: 3mf-explorer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::models
---

# Pair 3MF Explorer

## Trigger

3MF Explorer should send print requests.

## Outcome

Once pasted, Mark for print in 3MF Explorer reaches this Hub, even from another computer that reaches the library by another path.
