---
kind: alternate
routes:
  web: Web
steps:
  - text: Taps a planned block
    kind: actor
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product shows the copy's times, where its runtime came from, its deadline, colors and mounts, why it landed on that printer and what the next best printers would have cost
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - Runtime
          - Deadline
          - Colors
      - entity: printer
        effect: reads
        facts:
          - Name
      - entity: library-file
        effect: reads
        facts:
          - Run times
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Ask why a copy landed where it did

## Trigger

A placement looks odd.

## Outcome

Why here names the reason: finishes soonest, fewer spool changes, kept where it was, or pinned.
