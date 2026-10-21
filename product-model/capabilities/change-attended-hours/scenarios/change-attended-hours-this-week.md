---
kind: alternate
routes:
  web: Web
steps:
  - text: Picks a week, changes its days and presses This week only
    kind: actor
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: reads
        facts:
          - Week overrides
    contexts:
      web:
        place: hub::dashboard::dispatch
  - text: The Product keeps those hours for that calendar week alone and replans
    kind: product
    actor: farm-operator
    entities:
      - entity: dispatch-settings
        effect: changes
        facts:
          - Week overrides
    contexts:
      web:
        place: hub::dashboard::dispatch
---

# Change one week only

## Trigger

A holiday or a busy week.

## Outcome

That week uses its own hours; Clear this week's override goes back to the standing week.
