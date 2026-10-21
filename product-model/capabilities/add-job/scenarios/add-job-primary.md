---
kind: primary
routes:
  web: Web
steps:
  - text: Picks a library file under Add job, sets the copies, an optional deadline and Be here at the finish, and presses Add
    kind: actor
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
        place: hub::dashboard::dispatch
  - text: The Product creates a queued job with the file's colors and time estimate at normal priority
    kind: product
    actor: farm-operator
    entities:
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
      - entity: library-file
        effect: reads
        facts:
          - Colors needed
          - Estimated time
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: It plans the new copies across the farm
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Add a file to plan

## Trigger

Work is ordered.

## Outcome

The job is in the JOBS list and its copies are on the timeline.
