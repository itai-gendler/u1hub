---
kind: alternate
routes:
  web: Web
steps:
  - text: With a file selected, presses Print on best printer
    kind: actor
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Colors needed
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product names the printer and counts down five seconds
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
  - text: Presses Cancel, presses Print on best printer again, or selects another file
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product stops and says nothing was sent
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dash
---

# Cancel during the countdown

## Trigger

The named printer is not the one the operator wants.

## Outcome

Nothing was sent.
