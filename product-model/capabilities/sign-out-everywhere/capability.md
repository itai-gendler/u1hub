---
availability:
  - place: hub::dashboard
domain: settings
references:
  - kind: code
    role: implementation
    target: auth.js#mountAuth
  - kind: code
    role: implementation
    target: public/app.js#refreshAuthLine
---

# Sign out everywhere

Sign out everywhere under Access: ending every session on every device at once.
