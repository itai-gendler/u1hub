---
kind: primary
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
  - text: >-
      The Product plans the remaining copies of every queued job: earliest deadline first, priority breaking ties, on printers in service that can print them, each copy starting inside attended hours
      on the printer that finishes it soonest, a spool swap counting as twenty minutes
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - Remaining
          - Deadline
          - Priority
          - Runtime
          - Colors
          - Pinned printer
          - Pushed back behind
      - entity: dispatch-settings
        effect: reads
        facts:
          - Attended hours
          - Week overrides
          - Finish jobs
          - Completion target
      - entity: printer
        effect: reads
        facts:
          - Print state
          - Time left
      - entity: head
        effect: reads
        facts:
          - Loaded color
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: >-
      It draws a lane per printer with the running prints and the planned blocks, marking spools to mount before a block, a color another printer needs at the same time, and the wait for someone to
      clear the bed
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
      - entity: spool
        effect: reads
        facts:
          - Color name
      - entity: job
        effect: reads
        facts:
          - File
          - Printing on
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# See the day laid out

## Trigger

The operator plans the day.

## Outcome

Every printer, busy or idle, shows what it does next and when; a running print is never planned over or moved.

## Edge cases

- Prints that end while nobody is around are cleared one at a time, five minutes apart, in plan order.
- A copy stays on the printer it had in the last plan unless another finishes it thirty minutes sooner.
- Two jobs needing the same color at the same time are flagged, not serialized: the Hub assumes one roll per color.
