---
kind: validation
routes:
  web: Web
steps:
  - text: Tries Sign out everywhere
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::access
  - text: The Hub is Open, or a proxy holds the sessions
    kind: condition
    entities:
      - entity: access-settings
        effect: reads
        facts:
          - Access mode
    contexts:
      web:
        place: hub::dashboard::access
  - text: The Product offers nothing to sign out and says why
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::access
---

# No sessions to end

## Trigger

The Hub has no password.

## Outcome

The button stays unavailable outside Password mode.
