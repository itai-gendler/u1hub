---
kind: validation
routes:
  web: Web
steps:
  - text: Opens a printer's badge on a file, chooses rename and types a new name
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
  - text: The printer is printing or paused on that very file, the file is read-only, or the new name already exists on that printer
    kind: condition
    entities:
      - entity: printer-file
        effect: reads
        facts:
          - Printing now
          - Writable
          - Name
      - entity: printer
        effect: reads
        facts:
          - Print state
    contexts:
      web:
        place: hub::dashboard::files
  - text: The Product refuses and says why
    kind: product
    actor: farm-operator
    entities:
      - entity: printer-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::files
---

# Refuse to rename the file being printed

## Trigger

The copy is in use or protected, or the name is taken.

## Outcome

Nothing on the printer changes.
