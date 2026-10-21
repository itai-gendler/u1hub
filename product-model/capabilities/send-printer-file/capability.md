---
availability:
  - place: hub::dashboard
references:
  - kind: code
    role: implementation
    target: core/library.js#streamTransfer
  - kind: code
    role: implementation
    target: public/app.js#startTransfer
  - kind: code
    role: implementation
    target: core/print.js#progressWatchdog
---

# Send a printer file

Send to… on a printer's copy: copy it straight to another printer, or into the Hub library so it can be queued, planned and sent to any printer. The Hub carries the bytes itself; nothing is re-sliced.
