---
appliesTo:
  - type: capability
    id: deduct-filament
  - type: entity
    id: filament-use
    effect: creates
references:
  - kind: code
    role: implementation
    target: modules/resources.js#register
---

# Deductions touch only rolls with grams recorded

A finished print takes grams only off spools recorded in its heads that have grams left recorded, never below zero, and costs them only at a recorded price. A cancelled or failed print deducts nothing.

## Rationale

An invented number that then goes negative is worse than no number.
