---
kind: validation
routes:
  web: Web
steps:
  - text: Presses Start tunnel
    kind: actor
    actor: farm-operator
    entities:
      - entity: tunnel
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::remote-access
  - text: The Hub is Open, or in a proxy mode the tunnel would go around
    kind: condition
    entities:
      - entity: access-settings
        effect: reads
        facts:
          - Access mode
      - entity: tunnel
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::remote-access
  - text: The Product refuses and says to set a password first
    kind: product
    actor: farm-operator
    entities:
      - entity: tunnel
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::remote-access
---

# Refuse to publish an unprotected Hub

## Trigger

Remote access is tried before a password is set.

## Outcome

Nothing is published.
