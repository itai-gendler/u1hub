---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Add the fix on an open issue, writes what fixed it and saves
    kind: actor
    actor: farm-operator
    entities:
      - entity: logbook-entry
        effect: reads
        facts:
          - What happened
          - Fix
    contexts:
      web:
        place: hub::dashboard::logbook
  - text: The Product records the fix and when it was added
    kind: product
    actor: farm-operator
    entities:
      - entity: logbook-entry
        effect: changes
        facts:
          - Fix
    contexts:
      web:
        place: hub::dashboard::logbook
---

# Close an issue with what fixed it

## Trigger

The problem is solved.

## Outcome

The issue shows its fix, ready for the next search.
