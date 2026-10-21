---
availability:
  - place: hub::dashboard
domain: settings
references:
  - kind: code
    role: implementation
    target: tunnel.js#fetchBinary
  - kind: code
    role: implementation
    target: tunnel.js#binaryVersion
---

# Download cloudflared

The first press of the Remote access button: fetching Cloudflare's tunnel program.
