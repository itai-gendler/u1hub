---
entities:
  - entity: library-file
    shows:
      - Name
      - Colors needed
      - Grams
      - Estimated time
      - Pieces per plate
      - Thumbnail
  - entity: printer
    shows:
      - Name
      - Print state
      - Printing file
      - Progress
      - Time left
      - Layer
      - Bed temperature
      - Pause reason
      - Free storage
      - Plug power
      - Maintenance note
      - Plate objects
      - Down since
      - Address
    collects:
      - Bed temperature
  - entity: head
    shows:
      - Number
      - Loaded
      - Loaded color
      - Material
      - Official spool
    collects:
      - Loaded color
      - Material
  - entity: filament-memory
    shows:
      - Printed
      - Spools used
  - entity: spool
    shows:
      - Color name
      - Color
      - Brand
  - entity: selling-price
    shows:
      - Price per piece
      - Revenue
      - Per printer hour
      - Per gram
      - Margin
      - Below floor
    collects:
      - Price per piece
  - entity: upkeep-task
    shows:
      - Task
      - Due
references:
  - kind: code
    role: implementation
    target: public/index.html
  - kind: code
    role: implementation
    target: public/app.js#renderFleet
  - kind: code
    role: implementation
    target: public/app.js#renderJob
---

# Dash

The selected file's card and the fleet: one card per printer with its live state, progress, loaded heads, bed, camera, plug and upkeep, and the controls to send, pause, resume or cancel.
