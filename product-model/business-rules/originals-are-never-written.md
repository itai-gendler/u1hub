---
appliesTo:
  - type: capability
    id: convert-to-u1
  - type: capability
    id: open-in-orca
references:
  - kind: code
    role: implementation
    target: modules/models.js#register
---

# Converting or tuning never writes the original 3MF

Convert to U1 writes a separate copy beside the original, and Open in Orca with these settings writes a scratch copy that is removed after three days. The Hub's U1 template files are never listed, renamed or deleted.
