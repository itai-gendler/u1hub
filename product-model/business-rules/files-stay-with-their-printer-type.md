---
appliesTo:
  - type: capability
    id: print-file
  - type: capability
    id: upload-file
references:
  - kind: code
    role: implementation
    target: core/print.js
---

# A file is sent only to printers of its own type

A file in one printer type's folder is never sent to a printer of another type. A multi-color file aimed at a printer that reports a single extruder is sent only after a warning is confirmed.
