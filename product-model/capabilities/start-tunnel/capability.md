---
availability:
  - place: hub::dashboard
domain: settings
references:
  - kind: code
    role: implementation
    target: tunnel.js#startTunnel
  - kind: code
    role: implementation
    target: public/app.js#refreshTunnelLine
---

# Start the tunnel

Start tunnel under Remote access: an HTTPS address for the Hub from anywhere, with no router changes. Only a password-protected Hub goes on the internet.
