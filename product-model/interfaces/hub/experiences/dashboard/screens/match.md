---
entities:
  - entity: printer
    shows:
      - Name
      - Maintenance note
  - entity: head
    shows:
      - Loaded color
  - entity: library-file
    shows:
      - Name
      - Colors needed
references:
  - kind: code
    role: implementation
    target: public/app.js#renderMatch
---

# Match

Every online printer of the selected type with its loaded colors and the library files those colors can already print.
