---
kind: primary
routes:
  web: Web
steps:
  - text: Presses the delete mark on an entry and Delete it
    kind: actor
    actor: farm-operator
    entities:
      - entity: logbook-entry
        effect: reads
        facts:
          - What happened
    contexts:
      web:
        place: hub::dashboard::logbook
  - text: The Product removes the entry
    kind: product
    actor: farm-operator
    entities:
      - entity: logbook-entry
        effect: removes
    contexts:
      web:
        place: hub::dashboard::logbook
---

# Delete a mistaken entry

## Trigger

An entry was logged by mistake.

## Outcome

The entry is gone.
