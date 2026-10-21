---
availability:
  - place: hub::dashboard
domain: settings
references:
  - kind: code
    role: implementation
    target: modules/timelapse.js#register
  - kind: code
    role: implementation
    target: public/modules/timelapse-ui.js
---

# Change the timelapse folder

The Timelapses card in Settings: where finished videos go, and whether ffmpeg is installed on the Hub computer. Timelapses is a feature switched off until turned on.
