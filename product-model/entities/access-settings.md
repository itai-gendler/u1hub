---
singleton: true
domain: settings
references:
  - kind: code
    role: implementation
    target: auth.js#mountAuth
  - kind: code
    role: implementation
    target: public/auth.html
---

# Access settings

How the Hub decides who is in. Kept apart from the rest of the settings, so the settings the page reads never carry the password.

## Information kept

- **Access mode** — Open (no gate, the default), Password, Proxy (a reverse proxy signs people in) or Forward-auth (an identity header from Authelia or Authentik).
- **Password** — The one shared password, kept only as a salted hash.
- **Identity header** — In Forward-auth mode, the header the proxy sets; Remote-User unless changed.
- **Trusted proxies** — Up to 16 addresses or ranges allowed to report a visitor's address or identity header; this computer alone when empty.
