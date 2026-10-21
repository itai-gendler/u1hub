---
kind: validation
routes:
  web: Web
steps:
  - text: Types a password of fewer than four characters and presses Protect this Hub
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::access
  - text: The Product refuses
    kind: product
    actor: farm-operator
    entities:
      - entity: access-settings
        effect: reads
        facts:
          - Access mode
    contexts:
      web:
        place: hub::dashboard::access
---

# A password that is too short

## Trigger

A short password.

## Outcome

The access mode stays as it was.
