---
availability:
  - place: hub::dashboard
references:
  - kind: code
    role: implementation
    target: public/app.js#selectFile
  - kind: code
    role: implementation
    target: public/app.js#defaultMapping
  - kind: code
    role: implementation
    target: core/library.js#readTailAsync
  - kind: code
    role: implementation
    target: parser.js#parseGcodeMap
---

# Select a file

Choosing a library file to see what it needs before it goes anywhere: its plate picture, the colors and materials it prints with, and a suggested head for each color on every idle printer.
