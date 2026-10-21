---
appliesTo:
  - type: capability
    id: view-plan
  - type: capability
    id: clear-bed
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#findContention
---

# Dispatch assumes one roll of each color

Two planned copies that need the same color at the same time are flagged on the plan and when the bed is cleared, naming the color, the other printer and the file; they are not delayed for it. The grams on the Spools tab do not change this.

## Rationale

The shelf is only partly entered; counting rolls from it would turn a careful warning into a confident wrong one.
