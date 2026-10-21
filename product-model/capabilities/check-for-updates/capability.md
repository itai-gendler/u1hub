---
availability:
  - place: hub::dashboard
references:
  - kind: code
    role: implementation
    target: modules/updates.js#register
  - kind: code
    role: implementation
    target: public/modules/updates-ui.js
---

# Check for updates

Once a day the Hub fetches one small public file to see whether a newer release exists, sending nothing about the farm. One box turns it off, and off means no request at all.
