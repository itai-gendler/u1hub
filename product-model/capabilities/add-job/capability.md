---
availability:
  - place: hub::dashboard
domain: dispatch
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#createJob
  - kind: code
    role: implementation
    target: public/modules/dispatch-ui.js
---

# Add a job

Putting a file into Dispatch with how many copies are wanted: from the Add job row, from Send to Dispatch on a selected file, or from an Orca session that saved a gcode. Several files added together become one bundle.
