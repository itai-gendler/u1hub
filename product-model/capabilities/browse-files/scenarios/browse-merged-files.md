---
kind: primary
routes:
  web: Web
steps:
  - text: Opens the file list
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::files
  - text: The Product lists the library files of the selected type with the files stored on that type's printers, merged by name, newest first
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
          - Size
          - Modified
          - Thumbnail
          - Last printed
      - entity: printer-file
        effect: reads
        facts:
          - Name
          - Size
          - Modified
      - entity: printer
        effect: reads
        facts:
          - Name
      - entity: printer-type
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::files
---

# See every file the farm holds

## Trigger

The operator wants to see what can be printed.

## Outcome

Every gcode file is in one list; each row carries a badge for every printer that stores a copy, a printer-only badge when the Hub library has none, and when it was last printed.

## Edge cases

- A printer that does not answer is left out of the badges instead of blanking the list.
