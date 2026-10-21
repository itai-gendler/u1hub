---
kind: validation
routes:
  web: Web
steps:
  - text: Saves an entry without saying what happened
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::logbook
  - text: The Product asks to say what happened; nothing is logged
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::logbook
---

# An entry needs what happened

## Trigger

Save is pressed too soon.

## Outcome

Nothing is logged.
