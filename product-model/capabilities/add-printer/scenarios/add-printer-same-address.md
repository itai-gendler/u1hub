---
kind: validation
routes:
  web: Web
steps:
  - text: Saves two printers with the same address and port
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
          - Address
    contexts:
      web:
        place: hub::dashboard::printers
  - text: The Product refuses the whole save, naming both printers
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::printers
---

# Refuse two printers at one address

## Trigger

An address was pasted twice.

## Outcome

Nothing is written; one host with Moonraker on two ports is still allowed.
