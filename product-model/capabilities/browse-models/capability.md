---
availability:
  - place: hub::dashboard
domain: models
references:
  - kind: code
    role: implementation
    target: modules/models.js#register
  - kind: code
    role: implementation
    target: modules/models.js#sortItems
  - kind: code
    role: implementation
    target: modules/models.js#printCounts
  - kind: code
    role: implementation
    target: public/modules/models-ui.js
---

# Browse models

The Models tab: the shelf of 3MF project files behind the gcode library, each card with the plate render the designer saved in it, the colors it was painted with and the objects on its plate.
