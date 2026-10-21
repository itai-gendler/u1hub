---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses Scan QR label and points the camera at a spool's label
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product reads the spool the label names and shows its card
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Brand
          - Material
          - Color name
          - Color
          - Loaded in
    contexts:
      web:
        place: hub::dashboard::spools
---

# Scan a QR label

## Trigger

The roll has no RFID tag, or the phone has no NFC.

## Outcome

The same card an RFID spool opens.

## Edge cases

- A QR code that is not a Hub spool label is ignored with a message, never bound.
