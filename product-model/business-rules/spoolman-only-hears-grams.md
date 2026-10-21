---
appliesTo:
  - type: capability
    id: deduct-filament
  - type: capability
    id: import-from-spoolman
references:
  - kind: code
    role: implementation
    target: modules/spoolman.js#register
---

# The Hub sends Spoolman only the grams it used

Importing reads from Spoolman; the only thing ever sent back is, with write-back on, the grams a finished print used, as an amount used, never a weight, a name or a color. A roll gone or archived in Spoolman becomes inactive in the Hub, never deleted.
