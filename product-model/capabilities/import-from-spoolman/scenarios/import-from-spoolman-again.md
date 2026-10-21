---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses Import on the Spoolman card
    kind: actor
    actor: farm-operator
    entities:
      - entity: spoolman-connection
        effect: reads
        facts:
          - Last import
    contexts:
      web:
        place: hub::dashboard::spools
  - text: Some rolls were imported before
    kind: condition
    entities:
      - entity: spool
        effect: reads
        facts:
          - Origin
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product updates those spools from Spoolman instead of adding duplicates; a loaded spool stays loaded
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: changes
        facts:
          - Brand
          - Material
          - Color name
          - Color
          - Grams left
          - Price per roll
          - Active
      - entity: spoolman-connection
        effect: changes
        facts:
          - Last import
    contexts:
      web:
        place: hub::dashboard::spools
---

# Import again

## Trigger

Spoolman changed since the last import.

## Outcome

The Hub's copies match Spoolman again.

## Edge cases

- A roll archived in Spoolman, or gone from it, is marked inactive here, never deleted.
- A Spoolman spool with no color is skipped and named by its number.
