---
appliesTo:
  - type: capability
    id: send-printer-file
  - type: capability
    id: rename-library-file
  - type: capability
    id: rename-printer-file
  - type: capability
    id: convert-to-u1
  - type: capability
    id: rename-model
references:
  - kind: code
    role: implementation
    target: core/library.js#streamTransfer
---

# A copy or rename never overwrites a file

Wherever a file would land on a name that is taken, the Hub refuses and asks for one of them to be renamed or deleted first. A copy into the Hub library appears under its final name only once it is complete and the right size; a copy to another printer is checked for size once it lands.

## Rationale

A printer's upload replaces an existing name without complaint, which could replace the file a printer is printing.
