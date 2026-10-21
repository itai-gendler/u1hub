---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Discover on network
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::printers
  - text: >-
      The Product checks every address on the Hub's local networks on the U1's port and stock Moonraker's, and lists each printer found with its name, machine type and serial, marking the ones already
      added
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts:
          - Address
    contexts:
      web:
        place: hub::dashboard::printers
  - text: Adds a found printer
    kind: actor
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::printers
  - text: The Product fills in a new printer row with its address, ready to Save
    kind: product
    actor: farm-operator
    entities:
      - entity: printer
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::printers
---

# Find the farm's printers

## Trigger

Setting up the farm for the first time.

## Outcome

The printers are in the list without typing an address.
