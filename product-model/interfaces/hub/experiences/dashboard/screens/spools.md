---
entities:
  - entity: spool
    shows:
      - Brand
      - Material
      - Variant
      - Color name
      - Color
      - Colors
      - Hot end temperature
      - Bed temperature
      - Tags
      - Origin
      - Grams left
      - Net weight
      - Price per roll
      - Buy link
      - Notes
      - Loaded in
    collects:
      - Brand
      - Material
      - Variant
      - Color name
      - Color
      - Colors
      - Hot end temperature
      - Bed temperature
      - Grams left
      - Price per roll
      - Buy link
  - entity: printer
    shows:
      - Name
  - entity: head
    shows:
      - Number
      - Loaded color
  - entity: filament-use
    shows:
      - Printer
      - File
      - Finished
      - Grams per roll
      - Cost
      - Spoolman status
  - entity: filament-library
    shows:
      - Swatches
      - Last updated
      - My colors
  - entity: inventory-settings
    shows:
      - Deduct automatically
    collects:
      - Deduct automatically
  - entity: spoolman-connection
    shows:
      - Spoolman address
      - Write-back
      - Last import
    collects:
      - Spoolman address
      - Write-back
  - entity: tunnel
    shows:
      - Public address
references:
  - kind: code
    role: implementation
    target: public/index.html
  - kind: code
    role: implementation
    target: public/app.js#renderSpoolView
  - kind: code
    role: implementation
    target: public/modules/spoolman-ui.js
  - kind: code
    role: implementation
    target: public/modules/resources-ui.js
---

# Spools

Scanning and binding rolls, every bound spool with where it is loaded and its grams, price and buy link, the filament used by finished prints, and the Spoolman card.
