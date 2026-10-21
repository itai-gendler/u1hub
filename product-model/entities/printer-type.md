---
domain: settings
relations:
  - entity: printer
    verb: groups
    cardinality: one-to-many
  - entity: library-file
    verb: holds
    cardinality: one-to-many
references:
  - kind: code
    role: implementation
    target: core/config.js#validateTypes
  - kind: code
    role: implementation
    target: core/library.js
---

# Printer type

A family of printers that shares a gcode folder, an accent color and a switcher tab. The built-in U1 type uses the base folder; other types are in beta and work against stock Klipper and Moonraker.

## Information kept

- **Name** — The type's display name.
- **Accent color** — The color the dashboard wears while the type is selected.
- **Folder** — The type's own subfolder of the G-code folder, made when the type is added and never moved; the U1 type uses the G-code folder itself.
- **Built-in** — Yes for the U1 type only.
- **Printers** — How many printers belong to the type.
