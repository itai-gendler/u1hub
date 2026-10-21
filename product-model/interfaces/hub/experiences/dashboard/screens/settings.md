---
entities:
  - entity: hub-settings
    shows:
      - G-code folder
      - Features
      - Affiliate links
      - Sell floor per gram
      - Filament cost per gram
    collects:
      - G-code folder
      - Features
      - Affiliate links
      - Sell floor per gram
      - Filament cost per gram
  - entity: printer-type
    shows:
      - Name
  - entity: printer
    shows:
      - Name
references:
  - kind: code
    role: implementation
    target: public/index.html
  - kind: code
    role: implementation
    target: public/app.js#loadConfigUI
  - kind: code
    role: implementation
    target: public/modules/margin-ui.js
---

# Settings

The settings page's general sections: the G-code folder, features, supporting the project, worth-printing rates, diagnostics and this device's camera choice.
