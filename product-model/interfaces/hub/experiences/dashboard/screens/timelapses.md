---
entities:
  - entity: hub-settings
    shows:
      - Timelapse folder
    collects:
      - Timelapse folder
  - entity: timelapse
    shows:
      - Printer name
      - File
      - Frames
      - Video
references:
  - kind: code
    role: implementation
    target: public/modules/timelapse-ui.js
---

# Timelapses

Where finished videos go, whether ffmpeg was found, what is recording now and the recent videos.
