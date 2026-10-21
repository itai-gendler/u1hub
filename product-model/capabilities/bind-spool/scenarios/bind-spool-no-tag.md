---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses New roll (no tag), describes the filament and binds it
    kind: actor
    actor: farm-operator
    entities:
      - entity: filament-library
        effect: reads
        facts:
          - Swatches
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product makes the spool with no tag and offers its QR label to print
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: creates
        to: On the shelf
        facts:
          - Brand
          - Material
          - Variant
          - Color name
          - Color
          - Hot end temperature
          - Bed temperature
          - Origin
    contexts:
      web:
        place: hub::dashboard::spools
---

# Start a roll with no tag

## Trigger

Most filament arrives on a plain roll with nothing to scan.

## Outcome

The roll has an identity; the printed label is its tag.
