---
kind: primary
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
          - Spoolman address
          - Last import
    contexts:
      web:
        place: hub::dashboard::spools
  - text: The Product reads every spool from Spoolman, archived ones included
    kind: product
    actor: farm-operator
    entities:
      - entity: spoolman-connection
        effect: reads
        facts:
          - Spoolman address
      - entity: spool
        effect: reads
        facts: []
    contexts:
      web:
        place: hub::dashboard::spools
  - text: It makes one Hub spool per Spoolman spool with its brand, material, color and temperatures, and its grams left, net weight, price and location
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: creates
        to: On the shelf
        facts:
          - Brand
          - Material
          - Color name
          - Color
          - Colors
          - Hot end temperature
          - Bed temperature
          - Origin
          - Grams left
          - Net weight
          - Price per roll
          - Notes
          - Active
    contexts:
      web:
        place: hub::dashboard::spools
  - text: It notes what the import did
    kind: product
    actor: farm-operator
    entities:
      - entity: spoolman-connection
        effect: changes
        facts:
          - Last import
    contexts:
      web:
        place: hub::dashboard::spools
---

# Import the rolls Spoolman keeps

## Trigger

The farm already keeps its rolls in Spoolman.

## Outcome

The rolls are on the Hub's shelf without typing each one again.
