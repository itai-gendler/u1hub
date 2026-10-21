---
appliesTo:
  - type: entity
    id: print-request
    effect: creates
permits:
  - actors:
      - 3mf-explorer
  - actors:
      - farm-operator
references:
  - kind: code
    role: implementation
    target: modules/models.js#tokenMatches
  - kind: code
    role: implementation
    target: auth.js#mountAuth
---

# Only 3MF Explorer with the pairing token files print requests

The print request address is the one address outside the sign-in that another program calls; it checks the pairing token instead. A signed-in browser may call it too.
