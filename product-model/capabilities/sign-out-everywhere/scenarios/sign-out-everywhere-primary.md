---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Sign out everywhere and confirms
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
  - text: The Product ends every session, this one included, and shows the sign-in page
    kind: product
    actor: farm-operator
    entities:
      - entity: sign-in-session
        effect: removes
    contexts:
      web:
        place: hub::dashboard::access
---

# Lock out a lost phone

## Trigger

A phone went missing, or a browser was left signed in somewhere.

## Outcome

Every device has to enter the password again.
