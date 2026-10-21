---
references:
  - kind: code
    role: implementation
    target: core/records.js#loadQueue
  - kind: code
    role: implementation
    target: core/library.js
---

# Queue entry

One file on the shared Up next list above the file list: a reminder of what to print next, in order. Nothing on it starts by itself.

## Information kept

- **File** — The library file to print.
- **Added** — When it was put on the list.
- **Position** — Its place in the list.
