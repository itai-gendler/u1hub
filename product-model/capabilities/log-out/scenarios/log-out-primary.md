---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Log out on Access
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::access
  - text: The Product ends this browser's session
    kind: product
    actor: farm-operator
    entities:
      - entity: sign-in-session
        effect: removes
    contexts:
      web:
        place: hub::dashboard::access
---

# Sign this browser out

## Trigger

A shared computer.

## Outcome

The next visit asks for the password.
