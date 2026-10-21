---
entities:
  - entity: library-file
    shows:
      - Name
      - Size
      - Modified
      - Thumbnail
      - Last printed
    collects:
      - Name
  - entity: printer-file
    shows:
      - Name
      - Size
      - Modified
    collects:
      - Name
  - entity: printer
    shows:
      - Name
  - entity: printer-type
    shows:
      - Name
      - Accent color
  - entity: queue-entry
    shows:
      - File
      - Position
references:
  - kind: code
    role: implementation
    target: public/app.js#renderList
  - kind: code
    role: implementation
    target: public/app.js#renderQueue
---

# File list

The list beside every tab: the selected printer type's switcher, the filter and sort, Up next, and every library and printer file with its thumbnail, badges and actions.
