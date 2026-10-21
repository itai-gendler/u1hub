---
kind: validation
routes:
  web: Web
steps:
  - text: Opens a printer's badge on a file, chooses delete and confirms
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
  - text: The printer is printing or paused on that file, or the file is read-only
    kind: condition
    entities:
      - entity: printer-file
        effect: reads
        facts:
          - Printing now
          - Writable
      - entity: printer
        effect: reads
        facts:
          - Print state
    contexts:
      web:
        place: hub::dashboard::files
  - text: The Product refuses and says the file is the active print or read-only
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

# Refuse to delete the file being printed

## Trigger

The copy is the one a printer is working from.

## Outcome

The running print's file stays where it is.
