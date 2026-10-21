---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Tap to scan a spool tag and holds a spool's tag to the phone
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: 'The Product finds the spool the tag belongs to and shows its card: brand, material, color, temperatures, and the printer and head it is loaded in'
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Tags
          - Brand
          - Material
          - Color name
          - Color
          - Hot end temperature
          - Bed temperature
          - Loaded in
      - entity: printer
        effect: reads
        facts: []
      - entity: head
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
---

# Tap a known tag

## Trigger

A roll is in hand and the operator wants to know what it is or load it.

## Outcome

The spool's card is open with Load here for every printer's heads.
