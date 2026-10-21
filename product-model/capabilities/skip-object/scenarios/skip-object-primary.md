---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Plate on a printing card
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
          - Plate objects
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product draws the objects on the plate from the front of the bed, marking the one printing now and the ones already skipped
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Plate objects
    contexts:
      web:
        place: hub::dashboard::plate
  - text: Taps an object and confirms
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Plate objects
    contexts:
      web:
        place: hub::dashboard::plate
  - text: The Product asks the printer to skip that object
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Plate objects
    contexts:
      web:
        place: hub::dashboard::plate
---

# Skip a failed part mid-print

## Trigger

One part on a full plate has come loose.

## Outcome

That object stops printing and the rest of the plate keeps going; a skip cannot be undone.
