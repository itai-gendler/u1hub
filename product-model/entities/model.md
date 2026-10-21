---
domain: models
relations:
  - entity: print-request
    verb: is requested in
    cardinality: one-to-one
  - entity: orca-session
    verb: is opened in
    cardinality: one-to-many
references:
  - kind: code
    role: implementation
    target: modules/models.js#identity
  - kind: code
    role: implementation
    target: modules/models.js#register
---

# Model

A 3MF project file on the Models shelf, the files not yet sliced, organized by designer.

## Information kept

- **File** — Its place in the models folder.
- **Designer** — From the folder, unless renamed under Designer names or set under Attributes.
- **Name** — From the folder, unless set under Attributes.
- **Plate render** — The plate picture the designer saved in the file.
- **Colors** — The filament colors the project was painted with.
- **Objects** — The objects on its plate.
- **Size** — The file's size.
- **Added** — When the file arrived on the shelf.
- **Printed count** — How many completed jobs in the printers' own history were sliced from it.
