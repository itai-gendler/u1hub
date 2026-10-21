---
kind: validation
routes:
  web: Web
steps:
  - text: Names a type whose folder name another type already uses
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer-type
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::printers
  - text: The Product refuses, since that folder is locked to the other type
    kind: product
    actor: farm-operator
    entities:
      - entity: printer-type
        effect: reads
        facts:
          - Folder
    contexts:
      web:
        place: hub::dashboard::printers
---

# A name that clashes

## Trigger

Two names make the same folder name.

## Outcome

No type is added.
