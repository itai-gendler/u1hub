---
appliesTo:
  - type: capability
    id: run-pre-flight
  - type: capability
    id: suggest-settings
references:
  - kind: code
    role: implementation
    target: modules/advisor.js#register
  - kind: doc
    role: intent
    target: README.md
---

# AI buttons send only a short brief, only when pressed

Nothing goes to Anthropic until a person presses an AI button, and then only a brief: settings, filaments, measured numbers, the loadout and, for a 3MF, its plate picture; never the gcode, the meshes or the printers' addresses. The operator's own key is used, and the same file on the same loadout is answered from the local store for free.
