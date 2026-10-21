---
references:
  - kind: code
    role: implementation
    target: core/library.js#listOnboard
  - kind: code
    role: implementation
    target: core/library.js#printerFileOpGuard
---

# Printer file

A gcode file stored on a printer's own storage, listed beside the Hub library in one merged list.

## Information kept

- **Name** — The file's path on the printer.
- **Size** — The file's size.
- **Modified** — When the file last changed.
- **Writable** — Whether the printer allows it to be changed.
- **Printing now** — Yes while the printer is printing it or paused on it.
