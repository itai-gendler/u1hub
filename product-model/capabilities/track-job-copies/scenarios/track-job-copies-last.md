---
kind: alternate
routes:
  web: Web
steps:
  - text: A printer holding a job's last copy reports complete with that job's file
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
  - text: The Product finishes the job and takes it off the list
    kind: product
    entities:
      - entity: job
        effect: removes
        from: Printing
      - entity: library-file
        effect: changes
        facts:
          - Run times
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# The last copy completes

## Trigger

The order is done.

## Outcome

The job leaves Dispatch; its bed still offers Bed cleared → next.
