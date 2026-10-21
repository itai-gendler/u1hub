---
availability:
  - place: hub::dashboard
references:
  - kind: code
    role: implementation
    target: modules/notify.js#compose
  - kind: code
    role: implementation
    target: core/events.js
  - kind: code
    role: implementation
    target: modules/logbook.js#register
---

# Send phone notifications

What reaches the phone through ntfy, on its own, for the events chosen.
