---
entities:
  - entity: model
    shows:
      - File
      - Designer
      - Name
      - Plate render
      - Colors
      - Objects
      - Size
      - Added
      - Printed count
    collects:
      - Designer
      - Name
  - entity: print-request
    shows:
      - Designer
      - Title
      - Requested at
      - Gcode
      - Pieces
  - entity: orca-session
    shows:
      - Model file
      - Saved gcode
      - Verified
      - Tuned copy
      - Queued job
  - entity: models-settings
    shows:
      - Models folder
      - Orca location
      - U1 template
      - Designer names
      - Pairing token
    collects:
      - Models folder
      - Orca location
      - U1 template
      - Designer names
  - entity: library-file
    shows:
      - Name
      - Linked model
      - Link verified
    collects:
      - Linked model
  - entity: printer
    shows:
      - Name
references:
  - kind: code
    role: implementation
    target: public/modules/models-ui.js
---

# Models

The shelf of 3MF files: designers, filter and sort, the cards, Requested, the Opened in Orca strip, settings suggestions and the Folder panel.
