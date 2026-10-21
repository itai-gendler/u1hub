---
kind: primary
routes:
  web: Web
steps:
  - text: Chooses rename on a library file and types a new name
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
  - text: The Product renames the file, adding .gcode to a bare name
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: changes
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::files
  - text: Its Up next entries and its last-printed time follow it to the new name
    kind: product
    actor: farm-operator
    entities:
      - entity: queue-entry
        effect: changes
        facts:
          - File
      - entity: library-file
        effect: reads
        facts:
          - Last printed
    contexts:
      web:
        place: hub::dashboard::files
---

# Rename a file and keep its history

## Trigger

A file's name is wrong or unclear.

## Outcome

The file has its new name and keeps its place on Up next and its print history.

## Edge cases

- A change of capital letters only is allowed.
