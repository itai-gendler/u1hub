---
kind: primary
routes:
  web: Web
steps:
  - text: A printer holding a job's copy reports complete with that job's file
    kind: condition
    unattended: true
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
          - Printing file
      - entity: job
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product counts one copy done and records how long it really took for the file
    kind: product
    entities:
      - entity: job
        effect: changes
        from: Printing
        to: Queued
        facts:
          - Remaining
          - Printing on
      - entity: library-file
        effect: changes
        facts:
          - Run times
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: It marks the printer's bed as waiting to be cleared
    kind: product
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# A copy completes

## Trigger

A planned print finishes.

## Outcome

One fewer copy remains, the printer's lane offers Bed cleared → next, and the file's next copies are planned at its real time once it has two runs.

## Edge cases

- A copy that completed while the Hub was stopped is counted at the next start.
- A file never run on the farm borrows the printer's usual ratio once that printer has three runs.
