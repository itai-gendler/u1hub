---
kind: primary
routes:
  web: Web
steps:
  - text: Presses the remove mark on an Up next entry
    kind: actor
    actor: farm-operator
    entities:
      - entity: queue-entry
        effect: reads
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::files
  - text: The Product takes the entry off the list
    kind: product
    actor: farm-operator
    entities:
      - entity: queue-entry
        effect: removes
    contexts:
      web:
        place: hub::dashboard::files
---

# Take a file off Up next

## Trigger

A lined-up file is no longer wanted next.

## Outcome

The entry is gone; the file stays in the library.
