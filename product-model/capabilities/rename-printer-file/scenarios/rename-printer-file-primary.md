---
kind: primary
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
  - text: The Product asks the printer live what it is printing and checks the file is writable
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
          - Printing file
      - entity: printer-file
        effect: reads
        facts:
          - Writable
          - Printing now
    contexts:
      web:
        place: hub::dashboard::files
  - text: The Product renames the copy on the printer's storage, adding .gcode to a bare name
    kind: product
    actor: farm-operator
    entities:
      - entity: printer-file
        effect: changes
        facts:
          - Name
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::files
---

# Rename a copy on a printer

## Trigger

A copy on a printer has the wrong name.

## Outcome

The copy on that printer has the new name; the Hub library is untouched.
