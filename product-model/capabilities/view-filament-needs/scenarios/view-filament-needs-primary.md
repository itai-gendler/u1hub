---
kind: primary
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
  - text: The Product reads the file of every Queued, Printing or Paused job and adds up the grams by material and color for the copies still to print
    kind: product
    actor: farm-operator
    entities:
      - entity: job
        effect: reads
        facts:
          - File
          - Remaining
      - entity: library-file
        effect: reads
        facts:
          - Colors needed
    contexts:
      web:
        place: hub::dashboard::resources
  - text: 'It matches each color to a spool: a color mapping first, then the same color in the same material, then the nearest color within a small difference; anything further is left unassigned'
    kind: product
    actor: farm-operator
    entities:
      - entity: color-mapping
        effect: reads
        facts:
          - Slicer color
          - Spool
      - entity: spool
        effect: reads
        facts:
          - Color
          - Material
          - Active
    contexts:
      web:
        place: hub::dashboard::resources
  - text: It shows for each color what is needed, what is on hand and the shortfall in grams, rolls and money, shortfall first
    kind: product
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Grams left
          - Net weight
          - Price per roll
    contexts:
      web:
        place: hub::dashboard::resources
---

# See what to buy for the schedule

## Trigger

The operator wants to order filament before the schedule runs dry.

## Outcome

The table says what to buy, color by color; the same count is the badge on the Resources tab.
