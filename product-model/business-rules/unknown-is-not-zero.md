---
appliesTo:
  - type: capability
    id: view-filament-needs
  - type: entity
    id: spool
    effect: reads
    facts:
      - Grams left
      - Price per roll
references:
  - kind: code
    role: implementation
    target: modules/resources.js#buildRows
  - kind: code
    role: implementation
    target: modules/resources.js#matchSpool
---

# An unknown amount is never shown as zero

Grams nobody entered show blank, not zero, and no shortfall is reported against them unless Assume empty is turned on; a price nobody entered is never assumed; a color further than the matching limit from every spool is left unassigned rather than guessed.

## Rationale

An honest gap beats a wrong shopping list.
