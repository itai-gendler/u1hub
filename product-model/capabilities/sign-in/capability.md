---
availability:
  - place: hub::sign-in
domain: settings
references:
  - kind: code
    role: implementation
    target: auth.js#checkPassword
  - kind: code
    role: implementation
    target: auth.js#rateLimited
  - kind: code
    role: implementation
    target: public/auth.html
---

# Sign in

Entering the Hub's password while it is password-protected.
