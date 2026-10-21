---
kind: primary
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
  - text: The Product deletes the copy from the printer's storage
    kind: product
    actor: farm-operator
    entities:
      - entity: printer-file
        effect: removes
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::files
---

# Delete a copy from a printer

## Trigger

A printer's storage is filling up, or a copy is obsolete.

## Outcome

The copy is gone from that printer; the library and other printers keep theirs.
