---
appliesTo:
  - type: capability
    id: record-timelapse
  - type: entity
    id: timelapse
references:
  - kind: code
    role: implementation
    target: modules/timelapse.js#register
---

# Only a finished print becomes a timelapse

Frames of a cancelled or failed print, or too few usable frames, are thrown away.
