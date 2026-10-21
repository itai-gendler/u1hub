---
entities:
  - entity: tunnel
    shows:
      - Tunnel mode
      - Public hostname
      - Start with Hub
      - Public address
      - cloudflared
    collects:
      - Tunnel mode
      - Tunnel token
      - Public hostname
      - Start with Hub
  - entity: access-settings
    shows:
      - Access mode
references:
  - kind: code
    role: implementation
    target: public/app.js#refreshTunnelLine
---

# Remote access

The tunnel's state and address, its kind, token and hostname, and Start with Hub.
