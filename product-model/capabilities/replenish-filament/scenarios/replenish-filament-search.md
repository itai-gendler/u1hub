---
kind: primary
routes:
  web: Web
steps:
  - text: Presses Replenish on Amazon on a short row
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Brand
          - Material
          - Color name
    contexts:
      web:
        place: hub::dashboard::resources
  - text: The spool has no buy link
    kind: condition
    entities:
      - entity: spool
        effect: reads
        facts:
          - Buy link
    contexts:
      web:
        place: hub::dashboard::resources
  - text: The Product opens an Amazon search for the brand, material and color, carrying the affiliate tag while affiliate links are on
    kind: product
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - Affiliate links
    contexts:
      web:
        place: hub::dashboard::resources
---

# Search for the filament

## Trigger

A color is short for the schedule.

## Outcome

A search for that filament is open in a new tab; it is a search, never presented as a listing the Hub checked.
