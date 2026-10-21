---
kind: validation
routes:
  web: Web
steps:
  - text: Chooses a mode other than Password
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
  - text: The tunnel is running
    kind: condition
    entities:
      - entity: tunnel
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::access
  - text: 'The Product refuses: the tunnel delivers anyone on the internet straight to the Hub, past any proxy, so it must be stopped first'
    kind: product
    actor: farm-operator
    entities:
      - entity: tunnel
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::access
---

# Refuse to drop the password while the tunnel runs

## Trigger

Someone tries to open up a Hub that is on the internet.

## Outcome

The password stays on.
