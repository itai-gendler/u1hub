---
appliesTo:
  - type: capability
    id: add-printer
  - type: capability
    id: edit-printer
references:
  - kind: code
    role: implementation
    target: core/settings.js
  - kind: code
    role: implementation
    target: core/network.js#printerOrigin
---

# Two printers never share one address

A save with two printers at the same host and port is refused and names both; the same host on two ports is two printers.
