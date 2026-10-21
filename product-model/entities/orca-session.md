---
domain: models
references:
  - kind: code
    role: implementation
    target: modules/models.js#openSession
---

# Orca session

A model opened in Snapmaker Orca from the Hub, with the Hub watching the gcode folder for what Orca saves. It shows on the Models tab under Opened in Orca.

## Information kept

- **Model file** — The model that was opened.
- **Opened at** — When Orca was launched.
- **Saved gcode** — The gcode Orca saved for it.
- **Verified** — Whether the saved gcode's title matched the model's.
- **Tuned copy** — Opened as a copy with suggested settings filled in, and what was applied.
- **Queued job** — The Dispatch job it was sent to, once sent.

## States

### Watching

Orca is open and nothing has been saved yet.

### Saved

A gcode was saved and linked to the model.

### Timed out

Nothing was saved within half an hour.
