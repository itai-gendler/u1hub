---
kind: edge
routes:
  web: Web
steps:
  - text: Opens a printer's badge on a file, chooses Send to… and picks a destination
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer-file
        effect: reads
        facts:
          - Name
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::files
  - text: Either side stops moving data for 30 seconds, or goes quiet for 60
    kind: condition
    entities:
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::files
  - text: The Product stops the copy, says it stalled and removes any half-copied library file
    kind: product
    actor: farm-operator
    entities:
      - entity: printer-file
        effect: reads
        facts:
          - Name
      - entity: library-file
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::files
---

# A copy that stops moving is stopped

## Trigger

A printer drops off the network mid-copy.

## Outcome

The copy fails with a plain message and the file is free to rename or delete again.
