---
kind: primary
routes:
  web: Web
steps:
  - text: Clears the bed and presses Bed cleared → next on that printer's lane
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product hands back the next copy planned for that printer
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - File
          - Copies
          - Remaining
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: It lists the spools to mount first and any color another printer needs at the same time, and asks to set it up
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Color name
      - entity: job
        effect: reads
        facts:
          - Colors
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: Confirms
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product selects the job's file on the Dash and scrolls to that printer's card to confirm the heads
    kind: product
    actor: farm-operator
    entities:
      - entity: library-file
        effect: reads
        facts:
          - Name
      - entity: printer
        effect: reads
        facts:
          - Name
      - entity: head
        effect: reads
        facts: []
      - entity: job
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
---

# Set up the next planned copy

## Trigger

A finished print came off the bed.

## Outcome

The next file is selected beside the printer's card, ready for Print; nothing has started yet.
