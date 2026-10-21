---
type: api
actors:
  - 3mf-explorer
entryPoints:
  - api: /api/models/print-request
references:
  - kind: code
    role: implementation
    target: modules/models.js#relOnShelf
  - kind: doc
    role: intent
    target: README.md
---

# Print request API

The one address another program calls: 3MF Explorer's server posts a model marked for print here, with the Hub's pairing token instead of a sign-in.
