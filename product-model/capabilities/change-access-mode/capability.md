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
    target: public/auth.html
  - kind: code
    role: implementation
    target: tunnel.js
---

# Change access

Manage access: protecting the Hub with a password, handing sign-in to a reverse proxy, or keeping it open. Any change ends every session signed in before it.
