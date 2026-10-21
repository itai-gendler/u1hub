---
kind: validation
routes:
  web: Web
steps:
  - text: Types a wrong password and presses Unlock
    kind: actor
    actor: visitor
    entities: []
    contexts:
      web:
        place: hub::sign-in::password-required
  - text: The Product says the password is wrong
    kind: product
    actor: visitor
    entities: []
    contexts:
      web:
        place: hub::sign-in::password-required
---

# A wrong password

## Trigger

A temperature typed with an extra digit.

## Outcome

No session is opened.
