---
kind: alternate
routes:
  web: Web
steps:
  - text: Adds two or more files under Add job, names the bundle, sets a deadline and presses Add
    kind: actor
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
      - entity: bundle
        effect: reads
        facts: []
      - entity: job
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product creates the bundle and one queued job per file together, all sharing the bundle's deadline
    kind: product
    actor: farm-operator
    entities:
      - entity: bundle
        effect: creates
        facts:
          - Name
          - Deadline
      - entity: job
        effect: creates
        to: Queued
        facts:
          - File
          - Copies
          - Remaining
          - Deadline
          - Priority
          - Be here at the finish
          - Runtime
          - Colors
          - Source
        with: bundle
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Add several plates as one bundle

## Trigger

A delivery needs several plates, such as a body and a head.

## Outcome

The plates are planned to land by the one deadline.

## Edge cases

- One missing file refuses the whole bundle.
- At most 24 files make one bundle.
- Files with different counts keep their own counts inside the bundle.
