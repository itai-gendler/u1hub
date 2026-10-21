---
kind: primary
routes:
  api: API
steps:
  - text: Asks the health address
    kind: actor
    actor: watchdog
    entities: []
    contexts:
      api:
        place: health-check
  - text: The Product answers ok with its version, how many printers it has and how long it has run
    kind: product
    actor: watchdog
    entities:
      - entity: printer
        effect: reads
        facts: []
    contexts:
      api:
        place: health-check
---

# Answer a watchdog

## Trigger

A service watchdog or uptime monitor polls.

## Outcome

The monitor sees the Hub is up.
