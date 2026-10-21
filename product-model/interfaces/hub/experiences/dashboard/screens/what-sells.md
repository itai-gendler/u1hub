---
entities:
  - entity: selling-price
    shows:
      - File
      - Price per piece
      - Pieces
      - Revenue
      - Per printer hour
      - Per gram
      - Margin
      - Below floor
      - Saved
references:
  - kind: code
    role: implementation
    target: public/modules/margin-ui.js
---

# What sells

Every priced file, most profitable per printer hour first, with totals and a CSV export.
