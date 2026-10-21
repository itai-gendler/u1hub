---
kind: primary
routes:
  web: Web
steps:
  - text: Chooses delete on a library file and confirms
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
  - text: The Product deletes the file and forgets when it was last printed, so a later file with the same name starts fresh
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: removes
    contexts:
      web:
        place: hub::dashboard::files
---

# Delete a file from the library

## Trigger

A file is no longer wanted.

## Outcome

The file is gone from the Hub library; any copy on a printer's storage is still there.
