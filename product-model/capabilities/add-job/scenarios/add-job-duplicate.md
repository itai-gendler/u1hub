---
kind: validation
routes:
  web: Web
steps:
  - text: Adds a file that already has a queued job outside a bundle
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
  - text: The same file is already waiting in the queue
    kind: condition
    entities:
      - entity: job
        effect: reads
        facts:
          - File
          - Remaining
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product refuses a second job and offers to add the copies to the one waiting
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - Remaining
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: Accepts
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product raises that job's copies
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: changes
        facts:
          - Copies
          - Remaining
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Add copies to the job already waiting

## Trigger

The same file is added again by mistake, or more copies are wanted.

## Outcome

One job with the higher count, never two jobs printing the same thing by accident.

## Edge cases

- A file whose copy is printing right now can be added again: printing another after this one is a normal ask.
