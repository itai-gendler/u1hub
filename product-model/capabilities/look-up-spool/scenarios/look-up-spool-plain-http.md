---
kind: edge
routes:
  web: Web
steps:
  - text: Opens the Spools tab on a phone over the Hub's plain http network address
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The browser grants NFC and the camera only on a secure address
    kind: condition
    entities: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product explains why scanning is off and how to open the Hub through the tunnel address, or as localhost on the Hub computer; typing a tag number still works
    kind: product
    actor: farm-operator
    entities:
      - entity: tunnel
        effect: reads
        facts:
          - Public address
    contexts:
      web:
        place: hub::dashboard::spools
---

# Scanning over plain http

## Trigger

QR scanning seems not to work on a phone.

## Outcome

The operator knows to use the tunnel address for scanning.
