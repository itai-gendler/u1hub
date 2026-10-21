---
singleton: true
domain: spools
references:
  - kind: code
    role: implementation
    target: rfid.js#mountRfid
  - kind: code
    role: implementation
    target: scripts/refresh-filament-db.js
---

# Filament library

The catalog a new spool is picked from: about 2,266 colorimeter-measured swatches from FilamentColors.xyz shipped with the Hub, plus the operator's own saved colors.

## Information kept

- **Swatches** — How many catalog colors there are.
- **Last updated** — When the catalog was last refreshed, or the shipped snapshot.
- **My colors** — Colors typed in by hand and saved for reuse.
