---
availability:
  - place: hub::dashboard
domain: logbook
references:
  - kind: code
    role: implementation
    target: modules/logbook.js#register
  - kind: code
    role: implementation
    target: core/events.js
---

# Log printer events

What the Logbook fills in by itself: a pause or error the printer reports with a reason, and when upkeep comes due. Taking a printer out of service also opens an entry (see Take a printer down for maintenance).
