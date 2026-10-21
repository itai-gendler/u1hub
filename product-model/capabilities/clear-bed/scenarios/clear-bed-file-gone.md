---
kind: validation
routes:
  web: Web
steps:
  - text: Presses Bed cleared → next on a printer's lane
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The next planned copy's file is no longer in the Hub library
    kind: condition
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
      - entity: job
        effect: reads
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product says the file is gone and how to put it back, or to remove the job; nothing is selected
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# The planned file left the library

## Trigger

The file was deleted after it was planned.

## Outcome

The operator is not sent to a Dash with nothing loaded.
