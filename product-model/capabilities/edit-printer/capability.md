---
availability:
  - place: hub::dashboard
domain: settings
references:
  - kind: code
    role: implementation
    target: core/settings.js
  - kind: code
    role: implementation
    target: core/printer-ids.js#idForIncoming
  - kind: code
    role: implementation
    target: modules/dispatch.js#ensureMapped
---

# Edit a printer

Changing a printer's name, address, type or plug under Printers. The printer keeps its identity, so what the Hub knows about it follows the machine.
