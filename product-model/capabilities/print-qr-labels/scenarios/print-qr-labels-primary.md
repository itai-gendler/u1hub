---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Print QR labels on the Spools tab
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: 'The Product lays out a label for every spool: its QR code, color, name and material'
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Color name
          - Color
          - Brand
          - Material
    contexts:
      web:
        place: hub::dashboard::qr-labels
  - text: Chooses a sheet or the M110 size and prints, or prints one label over Bluetooth
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::qr-labels
---

# Print labels for tagless rolls

## Trigger

New rolls need labels.

## Outcome

Each roll can be scanned like a tagged one.
