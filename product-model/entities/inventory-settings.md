---
singleton: true
domain: spools
references:
  - kind: code
    role: implementation
    target: modules/resources.js#makeStore
---

# Inventory settings

How the Hub treats the grams on the shelf.

## Information kept

- **Deduct automatically** — Whether finished prints take their grams off the rolls in the heads that printed them; on unless turned off.
- **Assume empty** — Whether a roll with no grams recorded counts as empty on the Resources tab; off unless turned on.
