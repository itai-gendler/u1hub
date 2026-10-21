---
availability:
  - place: hub::dashboard
domain: dash
references:
  - kind: code
    role: implementation
    target: modules/margin.js#quote
  - kind: code
    role: implementation
    target: modules/margin.js#register
  - kind: code
    role: implementation
    target: public/modules/margin-ui.js
---

# Save a selling price

Under every selected file one line says what its filament costs, the least it must sell for (per piece when the name carries the plate count) and what that is per printer hour. Typing what a piece really sells for turns that into real numbers, and Save keeps them for the What sells table.
