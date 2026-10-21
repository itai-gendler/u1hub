---
relations:
  - entity: queue-entry
    verb: is lined up as
    cardinality: one-to-many
  - entity: job
    verb: is planned as
    cardinality: one-to-many
  - entity: selling-price
    verb: is priced at
    cardinality: one-to-one
references:
  - kind: code
    role: implementation
    target: core/library.js
  - kind: code
    role: implementation
    target: parser.js#parseGcodeMap
  - kind: code
    role: implementation
    target: modules/margin.js#qtyFromName
---

# Library file

A sliced gcode file in the Hub library, the G-code folder of its printer type. Everything the Hub prints, plans and prices starts from one.

## Information kept

- **Name** — The file name; a count such as x24 in it is how many pieces are on the plate.
- **Size** — The file's size.
- **Modified** — When the file last changed.
- **Colors needed** — Each color the file prints with, its material and its grams, read from the slicer's settings in the file.
- **Pieces per plate** — The x number in the name, up to 999; one piece when there is none.
- **Grams** — The filament the whole file uses, from the slicer's totals.
- **Estimated time** — The slicer's printing time estimate.
- **Thumbnail** — The plate picture the slicer saved in the file.
- **Last printed** — When a printer last started it.
- **Linked model** — The Models tab 3MF it was sliced from, when known.
- **Link verified** — Whether the gcode's title matched that model's when it was linked.
- **Run times** — How long each of its last five completed copies really took, and on which printer.
