---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses AI pre-flight again on a file already reviewed for that printer
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: Neither the file's settings nor the heads' loadout changed since
    kind: condition
    entities:
      - entity: head
        effect: reads
        facts:
          - Loaded color
          - Material
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product answers from its local store without asking Claude
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dash
---

# The same file on the same loadout is free

## Trigger

The same check is asked for twice.

## Outcome

The earlier verdict shows at no cost; Ask again bypasses the store.
