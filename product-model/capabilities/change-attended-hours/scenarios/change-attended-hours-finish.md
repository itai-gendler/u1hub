---
kind: alternate
routes:
  web: Web
steps:
  - text: Sets Finish jobs to only while I am here
    kind: actor
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: reads
        facts:
          - Finish jobs
      - entity: job
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product plans every copy to start and end inside one attended block and replans
    kind: product
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: changes
        facts:
          - Finish jobs
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Only finish while someone is here

## Trigger

Prints should never sit finished on a bed overnight.

## Outcome

A copy too long for any block is reported as unplannable instead of given a slot it cannot keep.
