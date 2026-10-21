---
kind: edge
routes:
  web: Web
steps:
  - text: With a file selected, presses Print on a printer's card
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
  - text: The printer takes no data for 30 seconds, or never accepts the connection
    kind: condition
    entities:
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: 'The Product stops the upload and says which happened: stalled, or could not connect (unplugged, asleep or a wrong address)'
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
---

# A printer that stops taking data

## Trigger

A printer drops off the network or is switched off mid-upload.

## Outcome

The card says what went wrong and the file is free to rename or delete again.
