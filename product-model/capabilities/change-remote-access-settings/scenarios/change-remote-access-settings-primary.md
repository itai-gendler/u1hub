---
kind: primary
routes:
  web: Web
steps:
  - text: Picks Named tunnel, pastes the token from Cloudflare and the hostname, and ticks start with Hub
    kind: actor
    actor: farm-operator
    entities:
      - entity: tunnel
        effect: reads
        facts:
          - Tunnel mode
          - Public hostname
          - Start with Hub
    contexts:
      web:
        place: hub::dashboard::remote-access
  - text: The Product keeps them; the token is never shown again
    kind: product
    actor: farm-operator
    entities:
      - entity: tunnel
        effect: changes
        facts:
          - Tunnel mode
          - Tunnel token
          - Public hostname
          - Start with Hub
    contexts:
      web:
        place: hub::dashboard::remote-access
---

# Use a named tunnel

## Trigger

A stable address is wanted for phones and NFC scanning.

## Outcome

The next start uses the named tunnel.
