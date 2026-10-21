---
kind: validation
routes:
  web: Web
steps:
  - text: Saves a task with neither print hours nor days
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::logbook
  - text: The Product asks for an interval; nothing is added
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::logbook
---

# A task needs an interval

## Trigger

The interval was left blank.

## Outcome

Nothing is added.
