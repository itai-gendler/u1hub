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
    target: public/modules/logbook-ui.js
---

# Add an upkeep task

+ Add task on the Logbook's schedule: upkeep that comes round every so many print hours, every so many days, or both, for one printer or all of them. Suggested tasks are a click away and are starting points, not a printer maker's numbers.
