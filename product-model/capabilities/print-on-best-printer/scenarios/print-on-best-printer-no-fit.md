---
kind: validation
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
  - text: No idle printer in service can stand in for more than all but two of the colors, or none is idle
    kind: condition
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product says which printer came closest and what it is missing
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
      - entity: head
        effect: reads
        facts:
          - Loaded color
    contexts:
      web:
        place: hub::dashboard::dash
---

# No printer is close enough

## Trigger

The farm has the wrong rolls loaded for this file.

## Outcome

Nothing is sent, and the operator knows what to load and where.
