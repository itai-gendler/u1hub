---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Pause on a queued job
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
  - text: The Product holds the job and plans nothing for it
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: changes
        from: Queued
        to: Paused
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Hold a job back

## Trigger

A job waits on a customer's answer.

## Outcome

Its copies leave the timeline; the job stays in the list.

## Edge cases

- A paused job's filament is still counted on the Resources tab.
