---
availability:
  - place: hub::dashboard
references:
  - kind: code
    role: implementation
    target: core/library.js#listLibrary
  - kind: code
    role: implementation
    target: public/app.js#renderList
  - kind: code
    role: implementation
    target: core/util.js#nameMatcher
---

# Browse files

The file list beside every tab: the selected printer type's Hub library and every file stored on that type's printers, merged into one list by name with thumbnails, filtered and sorted.
