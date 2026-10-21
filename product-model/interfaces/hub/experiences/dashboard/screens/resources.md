---
entities:
  - entity: job
    shows:
      - File
      - Remaining
      - Deadline
  - entity: spool
    shows:
      - Brand
      - Material
      - Variant
      - Color name
      - Color
      - Grams left
      - Net weight
      - Price per roll
      - Buy link
    collects:
      - Grams left
      - Price per roll
      - Buy link
  - entity: color-mapping
    shows:
      - Slicer color
      - Spool
    collects:
      - Spool
  - entity: inventory-settings
    shows:
      - Assume empty
  - entity: hub-settings
    shows:
      - Affiliate links
references:
  - kind: code
    role: implementation
    target: public/modules/resources-ui.js
---

# Resources

Filament needed for the schedule, color by color, against what is on the shelf, shortfall first, with the affiliate note at the bottom.
