---
kind: alternate
routes:
  web: Web
steps:
  - text: An upkeep task comes due on a printer, with maintenance due chosen
    kind: condition
    unattended: true
    entities:
      - entity: upkeep-task
        effect: reads
        facts:
          - Task
          - Due
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::phone-notifications
  - text: The Product posts once that the task is due on that printer, how often it comes round and how long since it was done
    kind: product
    entities:
      - entity: upkeep-task
        effect: reads
        facts:
          - Every print hours
          - Every days
          - Last done
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::phone-notifications
---

# Tell the phone upkeep is due

## Trigger

A task's interval ran out.

## Outcome

One message; the next only after it is marked done and comes due again.
