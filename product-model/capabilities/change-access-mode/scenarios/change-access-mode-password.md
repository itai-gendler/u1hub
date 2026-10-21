---
kind: primary
routes:
  web: Web
steps:
  - text: On Access, types a password twice and presses Protect this Hub
    kind: actor
    actor: farm-operator
    entities:
      - entity: access-settings
        effect: reads
        facts:
          - Access mode
    contexts:
      web:
        place: hub::dashboard::access
  - text: The Product keeps the password, switches to Password mode and signs this browser in
    kind: product
    actor: farm-operator
    entities:
      - entity: access-settings
        effect: changes
        facts:
          - Access mode
          - Password
      - entity: sign-in-session
        effect: creates
        facts:
          - Expires
    contexts:
      web:
        place: hub::dashboard::access
---

# Protect the Hub with a password

## Trigger

The Hub is about to be reachable from outside, or the network is shared.

## Outcome

Every page and address asks for the password, except the sign-in page, the app icons, the health check and 3MF Explorer's print requests.
