---
kind: validation
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
  - text: Another library file already has that name, or the file is being sent to a printer
    kind: condition
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::files
  - text: The Product refuses and says why; nothing is renamed
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::files
---

# Refuse a rename that would collide

## Trigger

The new name is taken, or an upload of the file is under way.

## Outcome

Both files are as they were; the Hub never renames over an existing file.
