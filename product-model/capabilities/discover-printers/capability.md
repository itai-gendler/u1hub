---
availability:
  - place: hub::dashboard
domain: settings
references:
  - kind: code
    role: implementation
    target: core/network.js#probeMoonraker
  - kind: code
    role: implementation
    target: public/app.js#runDiscover
---

# Discover printers

⟳ Discover on network under Printers: finding Klipper printers on the Hub's local network instead of typing addresses.
