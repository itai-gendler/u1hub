---
kind: alternate
routes:
  web: Web
steps:
  - text: Chooses proxy mode, or forward-auth mode with the identity header, under running behind a reverse proxy
    kind: actor
    actor: farm-operator
    entities:
      - entity: access-settings
        effect: reads
        facts:
          - Access mode
          - Identity header
    contexts:
      web:
        place: hub::dashboard::access
  - text: The Product switches mode; in Forward-auth it lets in only requests that carry the header from a trusted proxy
    kind: product
    actor: farm-operator
    entities:
      - entity: access-settings
        effect: changes
        facts:
          - Access mode
          - Identity header
    contexts:
      web:
        place: hub::dashboard::access
---

# Let a reverse proxy sign people in

## Trigger

Authelia or Authentik already guards the network.

## Outcome

The Hub's own password is off; the proxy decides who is in.
