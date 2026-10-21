---
kind: alternate
routes:
  web: Web
steps:
  - text: Types grams left, a price per roll or a buy link into the spool's row
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Grams left
          - Price per roll
          - Buy link
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product saves the number on the spool
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: changes
        facts:
          - Grams left
          - Price per roll
          - Buy link
    contexts:
      web:
        place: hub::dashboard::spools
---

# Set grams left, price and buy link

## Trigger

A roll was weighed, or bought at a new price.

## Outcome

Resources and the per-print cost use the new numbers.

## Edge cases

- Emptying a field clears the number back to unknown.
