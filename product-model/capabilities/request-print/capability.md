---
availability:
  - place: print-request-api
domain: models
references:
  - kind: code
    role: implementation
    target: modules/models.js#relOnShelf
  - kind: code
    role: implementation
    target: modules/models.js#autoDispatch
  - kind: code
    role: implementation
    target: modules/models.js#tokenMatches
---

# Request a print

Mark for print in 3MF Explorer: its server posts the model to the Hub with the pairing token, and the request waits under Requested until a gcode from that model exists. Then one print of it is queued.
