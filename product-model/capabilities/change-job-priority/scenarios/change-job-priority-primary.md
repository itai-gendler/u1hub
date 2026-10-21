---
kind: primary
routes:
  web: Web
steps:
  - text: Picks a priority from 1 to 5 on a job
    kind: actor
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - Priority
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product keeps the priority and replans
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: changes
        facts:
          - Priority
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Hurry a job along

## Trigger

One undated job matters more than the others.

## Outcome

It moves ahead of lower priorities, never ahead of a job with an earlier deadline.
