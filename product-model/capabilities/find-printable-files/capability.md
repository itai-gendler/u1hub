---
availability:
  - place: hub::dashboard
references:
  - kind: code
    role: implementation
    target: public/app.js#renderMatch
  - kind: code
    role: implementation
    target: public/app.js#matchFile
  - kind: code
    role: implementation
    target: public/app.js#matchPrint
  - kind: code
    role: implementation
    target: core/library.js#paletteForFileAsync
---

# Find what a printer can print

The Match view: tap a printer to see which library files its loaded colors can already print, best match first, one tap from printing.
