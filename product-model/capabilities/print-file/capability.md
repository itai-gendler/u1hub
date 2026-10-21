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
    target: core/print.js#countPauses
  - kind: code
    role: implementation
    target: core/records.js#dequeueFile
  - kind: code
    role: implementation
    target: public/app.js#pushTo
  - kind: code
    role: implementation
    target: public/app.js#pollJob
---

# Print a file

Print on an idle printer's card: send the selected file, map each of its colors to a head, and start it. Every print the Hub starts starts this way, from a person's tap.
