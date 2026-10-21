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
    target: public/app.js#addPrinterRow
---

# Add a printer

+ Add manually under Printers: a machine with its name, address, printer type and optional smart plug, saved with the Settings Save.
