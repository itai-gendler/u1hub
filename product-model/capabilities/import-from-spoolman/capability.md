---
availability:
  - place: hub::dashboard
domain: spools
references:
  - kind: code
    role: implementation
    target: modules/spoolman.js#mapSpool
  - kind: code
    role: implementation
    target: rfid.js#upsertImported
  - kind: code
    role: implementation
    target: public/modules/spoolman-ui.js
---

# Import from Spoolman

Reading every roll from a Spoolman server into the Hub in one press. Spoolman stays the source for what it knows; importing twice updates the same spools.
