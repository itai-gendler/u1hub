---
appliesTo:
  - type: capability
    id: start-tunnel
  - type: capability
    id: change-access-mode
references:
  - kind: code
    role: implementation
    target: tunnel.js#startTunnel
  - kind: code
    role: implementation
    target: auth.js#mountAuth
---

# The tunnel runs only on a password-protected Hub

The tunnel starts only in Password mode, and while it runs the access mode cannot leave Password.

## Rationale

The tunnel delivers visitors straight to the Hub, past any reverse proxy.
