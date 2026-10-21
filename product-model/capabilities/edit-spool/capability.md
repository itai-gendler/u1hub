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
    target: modules/resources.js#register
  - kind: code
    role: implementation
    target: public/app.js#openSpoolEdit
---

# Edit a spool

Changing what the Hub knows about a roll in place: its identity from the edit form, and its grams left, price per roll and buy link straight in its row. Its tags and where it is loaded stay.
