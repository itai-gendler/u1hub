---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Start tunnel
    kind: actor
    actor: farm-operator
    entities:
      - entity: tunnel
        effect: reads
        facts:
          - Tunnel mode
    contexts:
      web:
        place: hub::dashboard::remote-access
  - text: The Hub is password-protected and cloudflared is downloaded
    kind: condition
    entities:
      - entity: access-settings
        effect: reads
        facts:
          - Access mode
      - entity: tunnel
        effect: reads
        facts:
          - cloudflared
    contexts:
      web:
        place: hub::dashboard::remote-access
  - text: The Product starts the tunnel, a quick one or the named one with its token
    kind: product
    actor: farm-operator
    entities:
      - entity: tunnel
        effect: changes
        from: 'Off'
        to: Starting
        facts:
          - Public address
    contexts:
      web:
        place: hub::dashboard::remote-access
  - text: Once a connection registers it shows the HTTPS address to copy
    kind: product
    actor: farm-operator
    entities:
      - entity: tunnel
        effect: changes
        from: Starting
        to: Running
        facts: []
    contexts:
      web:
        place: hub::dashboard::remote-access
---

# Reach the Hub from anywhere

## Trigger

The operator wants to check prints from outside.

## Outcome

The fleet, sending prints, cameras, spools and scheduling all work from the address; a quick tunnel's address changes each start.
