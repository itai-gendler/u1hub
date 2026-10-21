---
kind: edge
routes:
  web: Web
steps:
  - text: Opens Resources
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::resources
  - text: A matched spool has no grams left recorded, or no price
    kind: condition
    entities:
      - entity: spool
        effect: reads
        facts:
          - Grams left
          - Price per roll
    contexts:
      web:
        place: hub::dashboard::resources
  - text: The Product shows on hand as blank rather than zero and invents no shortfall; a roll with no price shows rolls to buy but no money and is left out of the total with a note
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Grams left
          - Price per roll
    contexts:
      web:
        place: hub::dashboard::resources
---

# Rolls nobody weighed

## Trigger

The shelf is only partly entered.

## Outcome

An honest gap instead of a wrong shopping list.

## Edge cases

- A job whose gcode cannot be read is listed as unresolved, with its copies.
- With Dispatch switched off there is no schedule to price, and the tab says so.
