---
appliesTo:
  - type: capability
    id: check-for-updates
  - type: entity
    id: hub-settings
    effect: changes
    facts:
      - Latest version
references:
  - kind: code
    role: implementation
    target: modules/updates.js#register
---

# The update check sends nothing about the farm

It is one plain fetch of a public file, at most daily unless pressed; off means no request is made.
