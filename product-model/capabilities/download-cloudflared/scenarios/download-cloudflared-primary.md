---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Download cloudflared under Remote access
    kind: actor
    actor: farm-operator
    entities:
      - entity: tunnel
        effect: reads
        facts:
          - cloudflared
    contexts:
      web:
        place: hub::dashboard::remote-access
  - text: The Product downloads the one pinned release from Cloudflare's releases, checks it is that release and keeps it beside the Hub
    kind: product
    actor: farm-operator
    entities:
      - entity: tunnel
        effect: changes
        facts:
          - cloudflared
    contexts:
      web:
        place: hub::dashboard::remote-access
---

# Fetch the tunnel program

## Trigger

Remote access is being set up.

## Outcome

The button now offers Start tunnel.

## Edge cases

- A download that does not check out is not kept.
