---
availability:
  - place: hub::dashboard
references:
  - kind: code
    role: implementation
    target: core/library.js#libRemove
  - kind: code
    role: implementation
    target: core/library.js#activePushOf
  - kind: code
    role: implementation
    target: public/app.js#libDelete
---

# Delete a library file

Deleting a file from the Hub library. Copies on printers are separate files and are not touched.
