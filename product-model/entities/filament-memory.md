---
domain: dash
references:
  - kind: code
    role: implementation
    target: core/records.js#pollPrintStarts
  - kind: code
    role: implementation
    target: core/print.js
---

# Filament memory

Which spools were in which heads the last time a file finished printing, recalled when the same file is selected again. It follows the file's content, so a renamed file keeps it and a re-sliced one starts over.

## Information kept

- **File** — The file it was recorded for.
- **Printed** — When that print finished.
- **Spools used** — The spool in each head, with its color and brand.
