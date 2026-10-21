---
availability:
  - place: hub::dashboard
domain: spools
references:
  - kind: code
    role: implementation
    target: rfid.js#normUid
  - kind: code
    role: implementation
    target: public/app.js#handleUid
  - kind: code
    role: implementation
    target: public/app.js#handleSpoolId
  - kind: code
    role: implementation
    target: public/app.js#startQrScan
---

# Look up a spool

Identifying a roll from the Spools tab: tap its RFID tag to the phone, scan the QR label the Hub printed for it, or type a tag number. A tag's number is only a serial; nothing proprietary is decoded.
