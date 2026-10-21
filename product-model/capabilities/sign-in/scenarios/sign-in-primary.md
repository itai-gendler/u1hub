---
kind: primary
routes:
  web: Web
steps:
  - text: Types the password and presses Unlock
    kind: actor
    actor: visitor
    entities: []
    contexts:
      web:
        place: hub::sign-in::password-required
  - text: The Product checks the password and signs this browser in for thirty days
    kind: product
    actor: visitor
    entities:
      - entity: access-settings
        effect: reads
        facts:
          - Password
      - entity: sign-in-session
        effect: creates
        facts:
          - Expires
    contexts:
      web:
        place: hub::sign-in::password-required
---

# Unlock the Hub

## Trigger

Opening the Hub on a new device, or after the session expired.

## Outcome

The browser is back on the page it was going to.
