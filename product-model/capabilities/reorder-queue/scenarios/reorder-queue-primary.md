---
kind: primary
routes:
  web: Web
steps:
  - text: Presses the up or down arrow on an Up next entry
    kind: actor
    actor: farm-operator
    entities:
      - entity: queue-entry
        effect: reads
        facts:
          - File
          - Position
    contexts:
      web:
        place: hub::dashboard::files
  - text: The Product moves the entry one place and keeps any entry another device added meanwhile
    kind: product
    actor: farm-operator
    entities:
      - entity: queue-entry
        effect: changes
        facts:
          - Position
    contexts:
      web:
        place: hub::dashboard::files
---

# Bump an entry up the list

## Trigger

Something on the list became more or less urgent.

## Outcome

Up next shows the new order everywhere.
