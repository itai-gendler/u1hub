---
availability:
  - place: hub::dashboard
domain: dash
references:
  - kind: code
    role: implementation
    target: core/print.js#uploadWithProgress
  - kind: code
    role: implementation
    target: public/app.js#pushTo
---

# Upload a file

Upload on an idle printer's card: send the selected file to that printer with its heads mapped, without starting it.
