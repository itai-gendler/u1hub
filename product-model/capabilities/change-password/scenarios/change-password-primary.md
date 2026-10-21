---
kind: primary
routes:
  web: Web
steps:
  - text: Types a new password on Access and presses Change password
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
  - text: The Product keeps the new password; every other session ends and this browser stays signed in
    kind: product
    actor: farm-operator
    entities:
      - entity: access-settings
        effect: changes
        facts:
          - Password
      - entity: sign-in-session
        effect: removes
        as: others
      - entity: sign-in-session
        effect: creates
        facts:
          - Expires
        as: this
    contexts:
      web:
        place: hub::dashboard::access
---

# Change the shared password

## Trigger

The password was shared too widely.

## Outcome

Only people who know the new password get back in.

## Edge cases

- A password shorter than four characters is refused.
