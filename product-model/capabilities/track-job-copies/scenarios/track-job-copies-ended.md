---
kind: edge
routes:
  web: Web
steps:
  - text: A printer holding a job's copy is cancelled, errors or goes back to standby
    kind: condition
    unattended: true
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
      - entity: job
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product frees the printer, keeps the copy owed and puts a notice on the job
    kind: product
    entities:
      - entity: job
        effect: changes
        from: Printing
        to: Queued
        facts:
          - Printing on
          - Notice
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# A copy ends without completing

## Trigger

A print failed or was cancelled.

## Outcome

The printer is free right away and the copy stays on the list with a note; the notice clears with OK or when the next copy completes.
