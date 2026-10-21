---
kind: validation
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
  - text: The file is on Up next, belongs to a Dispatch job with copies left, or is being sent to a printer
    kind: condition
    entities:
      - entity: queue-entry
        effect: reads
        facts:
          - File
      - entity: job
        effect: reads
        facts:
          - File
          - Remaining
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::files
  - text: 'The Product refuses and says what to clear first: the Up next entry, the Dispatch job, or the upload'
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
      - entity: job
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::files
---

# Refuse to delete a file that is in use

## Trigger

Something still points at the file.

## Outcome

The file stays, so no list or plan is left pointing at a file that is gone.
