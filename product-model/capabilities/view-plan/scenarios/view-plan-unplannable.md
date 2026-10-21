---
kind: edge
routes:
  web: Web
steps:
  - text: Opens Dispatch
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: 'No printer can take a copy: every printer is down for maintenance, none is online, or the job needs colors and no multi-color printer is in service'
    kind: condition
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
      - entity: job
        effect: reads
        facts:
          - Colors
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product lists the copy as unplannable with the real cause
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - File
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# A copy with no place

## Trigger

The farm cannot print a job at all.

## Outcome

The operator sees the cause, not a fault to hunt for.
