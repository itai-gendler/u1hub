---
singleton: true
domain: settings
references:
  - kind: code
    role: implementation
    target: tunnel.js#startTunnel
  - kind: code
    role: implementation
    target: tunnel.js#stopTunnel
---

# Tunnel

The Hub-managed Cloudflare tunnel that gives the Hub an HTTPS address from anywhere, with no router changes.

## Information kept

- **Tunnel mode** — Quick tunnel (no account, a new address each start) or Named tunnel (a stable hostname from a Cloudflare token).
- **Tunnel token** — The Cloudflare token for a named tunnel; never shown again once saved.
- **Public hostname** — The hostname a named tunnel answers on, for display.
- **Start with Hub** — Whether the tunnel starts with the Hub and is started again when it drops.
- **Public address** — The HTTPS address the Hub is reachable on while the tunnel runs.
- **cloudflared** — The one pinned, checked release of Cloudflare's tunnel program, downloaded beside the Hub.

## States

### Off

The Hub is reachable on the local network only.

### Starting

The tunnel program is running and no connection has registered yet.

### Running

Connected: the Hub is reachable over HTTPS.

### Failed

The tunnel stopped on its own or could not start; the reason is shown.
