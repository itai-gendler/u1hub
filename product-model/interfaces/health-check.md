---
type: api
actors:
  - watchdog
entryPoints:
  - api: /healthz
references:
  - kind: code
    role: implementation
    target: core/health.js
  - kind: doc
    role: intent
    target: README.md
---

# Health check

An address a watchdog or uptime monitor polls with no sign-in; it answers with the Hub's version and printer count.
