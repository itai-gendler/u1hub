---
availability:
  - place: hub::dashboard
domain: spools
references:
  - kind: code
    role: implementation
    target: rfid.js#cleanIdentity
  - kind: code
    role: implementation
    target: public/app.js#openBindPanel
  - kind: code
    role: implementation
    target: public/app.js#bindSpool
---

# Bind a spool

Giving a roll an identity once, so its tag or label resolves to it from then on: pick it from the filament library, type it in, take it from a loaded head, or start a roll with no tag at all.
