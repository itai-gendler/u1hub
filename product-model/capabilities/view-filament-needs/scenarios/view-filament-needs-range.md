---
kind: alternate
routes:
  web: Web
steps:
  - text: Picks 7, 14 or 30 days, or ticks deadline only
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::resources
  - text: The Product leaves out jobs whose own deadline falls outside the window; jobs with no deadline are still counted unless deadline only is ticked
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - Deadline
          - Remaining
    contexts:
      web:
        place: hub::dashboard::resources
---

# Narrow the schedule to the next days

## Trigger

Only the next week's needs matter for this order.

## Outcome

The table covers that window, and keeps the undated work in view by default.
