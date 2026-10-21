---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Stop tunnel
    kind: actor
    actor: farm-operator
    entities:
      - entity: tunnel
        effect: reads
        facts:
          - Public address
    contexts:
      web:
        place: hub::dashboard::remote-access
  - text: The Product stops the tunnel and any retry
    kind: product
    actor: farm-operator
    entities:
      - entity: tunnel
        effect: changes
        from: Running
        to: 'Off'
        facts:
          - Public address
    contexts:
      web:
        place: hub::dashboard::remote-access
---

# Take the Hub off the internet

## Trigger

Remote access is no longer wanted.

## Outcome

The Hub is on the local network only.
