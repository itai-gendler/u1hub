---
appliesTo:
  - type: capability
    id: change-password
  - type: capability
    id: change-access-mode
  - type: capability
    id: sign-out-everywhere
references:
  - kind: code
    role: implementation
    target: auth.js#credTag
---

# Changing the password or access mode ends every session

Every session is tied to the password and the access settings it was signed in under; a change ends all of them, and the browser that made a password change is signed in again on the spot.
