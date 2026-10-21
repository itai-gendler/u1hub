---
kind: validation
routes:
  web: Web
steps:
  - text: Presses Unlock after five wrong passwords within fifteen minutes
    kind: actor
    actor: visitor
    entities: []
    contexts:
      web:
        place: hub::sign-in::password-required
  - text: The Product refuses every try from that visitor for fifteen minutes
    kind: product
    actor: visitor
    entities: []
    contexts:
      web:
        place: hub::sign-in::password-required
---

# Too many wrong passwords

## Trigger

Repeated wrong passwords.

## Outcome

That visitor waits; others, the owner included, can still sign in.
