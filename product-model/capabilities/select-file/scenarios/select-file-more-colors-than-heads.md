---
kind: edge
routes:
  web: Web
steps:
  - text: Selects a library file in the list
    kind: actor
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::files
  - text: The file prints with more colors than a U1 has heads and is not a Full Spectrum file
    kind: condition
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Colors needed
      - entity: head
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product says the file needs a roll swap during the print or a re-slice
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Colors needed
    contexts:
      web:
        place: hub::dashboard::dash
---

# A file needs more colors than heads

## Trigger

A file sliced with five or more colors is selected.

## Outcome

The operator knows before sending that one head must be swapped mid-print or the file re-sliced.
