---
kind: primary
routes:
  web: Web
steps:
  - text: Presses forget on a spool and confirms
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Color name
          - Brand
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product removes the spool and frees its tags
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: removes
        from: On the shelf
    contexts:
      web:
        place: hub::dashboard::spools
---

# Forget a used-up roll

## Trigger

The roll is finished and thrown away.

## Outcome

The spool is gone; its grams and price are dropped the next time Resources is read, unless a color mapping still names it, which then shows as orphaned.
