---
kind: primary
routes:
  web: Web
steps:
  - text: Sets the blocks for each day, such as home 8-11 and back 17-22, and presses Save for every week
    kind: actor
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: reads
        facts:
          - Attended hours
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product keeps the week, merging overlapping blocks, and replans
    kind: product
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: changes
        facts:
          - Attended hours
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Set the standing week

## Trigger

The operator's real week has gaps.

## Outcome

Jobs start only inside those blocks from now on.

## Edge cases

- A block ending at 23:59 runs to midnight.
