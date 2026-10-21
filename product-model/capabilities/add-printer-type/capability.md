---
availability:
  - place: hub::dashboard
domain: settings
references:
  - kind: code
    role: implementation
    target: core/library.js
  - kind: code
    role: implementation
    target: core/config.js#slugify
---

# Add a printer type

+ Add printer type: naming a family of non-U1 Klipper printers. The Hub makes its folder, gives it the next accent color and adds its switcher tab. Other types are in beta.
