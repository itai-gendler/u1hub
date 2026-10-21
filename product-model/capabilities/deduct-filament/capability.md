---
availability:
  - place: hub::dashboard
domain: spools
references:
  - kind: code
    role: implementation
    target: modules/resources.js#register
  - kind: code
    role: implementation
    target: modules/spoolman.js#register
---

# Deduct filament used

When a print finishes, the grams each of the file's colors used come off the roll recorded in the head that printed it, with the cost at the price paid. Deliberately cautious: only rolls with grams recorded are touched.
