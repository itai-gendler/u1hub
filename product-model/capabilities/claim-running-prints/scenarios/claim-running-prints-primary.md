---
kind: primary
routes:
  web: Web
steps:
  - text: Presses claim running prints above the plan
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product first lets go of claims the printers contradict
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: changes
        from: Printing
        to: Queued
        facts:
          - Printing on
        as: stale
      - entity: printer
        effect: reads
        facts:
          - Print state
          - Printing file
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: It attaches each running or paused print to a queued job of the same file and printer type
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: changes
        from: Queued
        to: Printing
        facts:
          - Printing on
        as: claimed
      - entity: printer
        effect: reads
        facts:
          - Print state
          - Printing file
      - entity: printer-type
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: It reports what it released, what it claimed, what was already tracked and what is running untracked
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Match the farm to the queue

## Trigger

Dispatch was turned on while the farm was busy.

## Outcome

Running copies count against their jobs and are not planned again.

## Edge cases

- A printer down for maintenance is reported, never claimed.
- One printer holds one job at a time.
