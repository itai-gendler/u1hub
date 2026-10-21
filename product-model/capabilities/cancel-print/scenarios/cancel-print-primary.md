---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Cancel on a card and confirms
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
  - text: The Product asks the printer to cancel and holds a spinner on the button until the printer answers
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

# Cancel from the card

## Trigger

The print is failing or no longer wanted.

## Outcome

The printer stops; a Dispatch copy it was printing stays owed and the printer is free for the next job.
