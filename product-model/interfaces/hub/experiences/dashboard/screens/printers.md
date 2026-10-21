---
entities:
  - entity: printer-type
    shows:
      - Name
      - Accent color
      - Folder
      - Built-in
      - Printers
    collects:
      - Name
      - Accent color
  - entity: printer
    shows:
      - Name
      - Address
      - Smart plug
    collects:
      - Name
      - Address
      - Smart plug
references:
  - kind: code
    role: implementation
    target: public/app.js#renderTypeRows
  - kind: code
    role: implementation
    target: public/app.js#addPrinterRow
---

# Printers

The printer types and the printers in each, with Discover on network.
