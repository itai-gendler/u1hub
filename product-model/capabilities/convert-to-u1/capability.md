---
availability:
  - place: hub::dashboard
domain: models
references:
  - kind: code
    role: implementation
    target: modules/u1convert.js
  - kind: code
    role: implementation
    target: modules/models.js#register
---

# Convert to U1

Convert to U1 behind a card's menu: a U1 copy of a MakerWorld or other Bambu project beside it, keeping the designer's prime tower, walls, infill and supports on the U1's printer and filament presets.
