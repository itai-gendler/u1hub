---
domain: models
references:
  - kind: code
    role: implementation
    target: modules/models.js#autoDispatch
---

# Print request

A model someone marked for print in 3MF Explorer, waiting under Requested on the Models tab until its gcode exists.

## Information kept

- **Model file** — The requested model's place in the models folder.
- **Designer** — The designer 3MF Explorer named.
- **Title** — The title 3MF Explorer named.
- **Requested at** — When it was marked.
- **Gcode** — The library file that answered it.
- **Pieces** — The x number of that gcode.
- **Dispatched at** — When its job went into Dispatch.

## States

### Requested

Waiting for a gcode sliced from the model.

### Dispatched

One print of its gcode is in Dispatch.
