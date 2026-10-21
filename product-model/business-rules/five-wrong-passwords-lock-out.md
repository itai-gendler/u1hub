---
appliesTo:
  - type: capability
    id: sign-in
  - type: entity
    id: sign-in-session
    effect: creates
references:
  - kind: code
    role: implementation
    target: auth.js#rateLimited
  - kind: code
    role: implementation
    target: auth.js#clientKey
---

# Five wrong passwords lock that visitor out for fifteen minutes

Counted per visitor address; an address reported by a proxy counts only when the proxy is trusted.
