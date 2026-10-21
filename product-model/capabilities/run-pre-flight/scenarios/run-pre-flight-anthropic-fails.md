---
kind: edge
routes:
  web: Web
steps:
  - text: With a file selected, picks the printer and presses AI pre-flight
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
  - text: Anthropic refuses the key or does not answer within 90 seconds
    kind: condition
    entities: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product shows the error on the card; the file and the printer are untouched
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

# Claude does not answer

## Trigger

The key ran out of credit or the network is down.

## Outcome

The operator sees why there is no verdict and can still print.
