---
appliesTo:
  - type: capability
    id: print-file
  - type: capability
    id: upload-file
references:
  - kind: code
    role: implementation
    target: core/print.js#countPauses
---

# One head prints one color unless the file pauses to swap

Two of a file's colors may share a head only when they are the same color. Two different colors on one head are sent only when the file carries a filament-change pause (M600 or PAUSE), and only after the operator confirms; otherwise the send is refused.
