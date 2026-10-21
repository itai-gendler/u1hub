---
kind: alternate
routes:
  web: Web
steps:
  - text: With a new tag scanned, taps the spool it belongs to in the list of bound spools
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Color name
          - Brand
          - Variant
          - Tags
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product adds the tag to that spool without changing anything else about it
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: changes
        facts:
          - Tags
    contexts:
      web:
        place: hub::dashboard::spools
---

# Attach a second tag to a known spool

## Trigger

A roll carries both a maker's tag and a Hub sticker, or a reader sees its tag differently.

## Outcome

Both tags open the same spool; no duplicate is made.
