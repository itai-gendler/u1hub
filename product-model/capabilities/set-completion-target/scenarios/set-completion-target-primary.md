---
kind: primary
routes:
  web: Web
steps:
  - text: Picks a date and time under Finish everything by and presses Set
    kind: actor
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: reads
        facts:
          - Completion target
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product keeps the target as the deadline of every job that has none of its own
    kind: product
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: changes
        facts:
          - Completion target
      - entity: job
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: It reports how many copies make their deadline, the tightest margin and, for each miss, how late it lands, the biggest wait behind it and the move that would recover it
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - File
          - Deadline
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Ask whether everything makes Friday 5pm

## Trigger

A show or a customer pickup is coming.

## Outcome

The report says plainly what makes it, what does not and why: a queue ahead of it, a bed waiting to be cleared, a busy printer, attended hours, or a print simply too long.
