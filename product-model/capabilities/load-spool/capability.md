---
availability:
  - place: hub::dashboard
domain: spools
references:
  - kind: code
    role: implementation
    target: rfid.js#mountRfid
  - kind: code
    role: implementation
    target: public/app.js#loadSpoolIntoSlot
  - kind: code
    role: implementation
    target: public/app.js#showSpoolResult
---

# Load a spool

Load here on a spool's card: recording which printer and head a roll went into, so the Hub knows what is on every machine. Recording works for any printer, even an offline one, and can also set that head's color on a U1.
