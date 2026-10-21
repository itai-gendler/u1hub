---
kind: alternate
routes:
  web: Web
steps:
  - text: Opens a printer's badge on a file, chooses Send to… and picks Hub library
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
  - text: The Product copies the file into the library folder of that printer's type, putting it in place only once its size matches the printer's listing
    kind: product
    actor: farm-operator
    entities:
      - entity: printer-file
        effect: reads
        facts:
          - Name
          - Size
      - entity: printer
        effect: reads
        facts: []
      - entity: library-file
        effect: creates
        facts:
          - Name
          - Size
          - Modified
      - entity: printer-type
        effect: reads
        facts:
          - Folder
    contexts:
      web:
        place: hub::dashboard::files
---

# Copy a printer-only file into the Hub library

## Trigger

A file exists only on one printer and should be queued or sent elsewhere.

## Outcome

The file is in the Hub library and can be queued, planned and sent to any printer of its type; the library never shows a half-copied file.
