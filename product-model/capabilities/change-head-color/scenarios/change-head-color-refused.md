---
kind: validation
routes:
  web: Web
steps:
  - text: Taps a head's color and picks a new one
    kind: actor
    actor: farm-operator
    entities:
      - entity: head
        effect: reads
        facts:
          - Number
      - entity: printer
        effect: reads
        facts:
          - Name
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The printer is printing or paused, the head is empty, or it holds an official Snapmaker RFID spool
    kind: condition
    entities:
      - entity: printer
        effect: reads
        facts:
          - Print state
      - entity: head
        effect: reads
        facts:
          - Loaded
          - Official spool
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product refuses and says why; an official spool's color comes from its tag
    kind: product
    actor: farm-operator
    entities:
      - entity: head
        effect: reads
        facts:
          - Number
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::dash
---

# Refuse a head that cannot change

## Trigger

The head is busy, empty or tagged.

## Outcome

The head keeps its color.
