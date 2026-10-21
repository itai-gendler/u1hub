---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses Turn the gate off
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
  - text: The Product drops the password and switches to Open; every session ends
    kind: product
    actor: farm-operator
    entities:
      - entity: access-settings
        effect: changes
        facts:
          - Access mode
          - Password
      - entity: sign-in-session
        effect: removes
    contexts:
      web:
        place: hub::dashboard::access
---

# Turn the gate off

## Trigger

The Hub only lives on a trusted home network.

## Outcome

Anyone who can reach the Hub can use it.
