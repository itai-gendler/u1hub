---
appliesTo:
  - type: capability
    id: print-file
  - type: capability
    id: print-on-best-printer
  - type: capability
    id: clear-bed
  - type: capability
    id: track-job-copies
references:
  - kind: code
    role: implementation
    target: modules/dispatch.js#register
  - kind: code
    role: implementation
    target: core/records.js
---

# Every print starts with a person's tap

The Hub never starts a printer by itself. Up next is a reminder, Dispatch plans but does not start, and Bed cleared → next only selects the file beside the printer's card; Print, or the end of Print on best printer's countdown, is the start.

## Rationale

A U1's plate must be cleared between prints; a bed nobody cleared is a bed nobody can print on.
