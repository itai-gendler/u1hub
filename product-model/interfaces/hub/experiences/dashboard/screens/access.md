---
entities:
  - entity: access-settings
    shows:
      - Access mode
      - Identity header
      - Trusted proxies
    collects:
      - Access mode
      - Password
      - Identity header
      - Trusted proxies
references:
  - kind: code
    role: implementation
    target: public/auth.html
  - kind: code
    role: implementation
    target: public/app.js#refreshAuthLine
---

# Access

How the Hub is protected: the Access section of Settings with Sign out everywhere and trusted proxies, and Manage access, where a password is set or changed, a proxy mode chosen, the gate turned off, or the browser logged out.
