---
availability:
  - place: hub::dashboard
domain: settings
references:
  - kind: code
    role: implementation
    target: core/settings.js
  - kind: code
    role: implementation
    target: core/config.js#saveConfigFile
---

# Change the G-code folder

The G-code folder at the top of Settings: the slicer's output folder the Hub library reads.
