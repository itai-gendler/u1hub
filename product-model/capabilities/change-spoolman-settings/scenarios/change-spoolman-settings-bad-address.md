---
kind: validation
routes:
  web: Web
steps:
  - text: Types an address that does not start with http:// or https:// and saves
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product refuses and keeps the previous address
    kind: product
    actor: farm-operator
    entities:
      - entity: spoolman-connection
        effect: reads
        facts:
          - Spoolman address
    contexts:
      web:
        place: hub::dashboard::spools
---

# Refuse an address that is not http

## Trigger

The Spoolman address was pasted without its scheme.

## Outcome

The previous address stays.
