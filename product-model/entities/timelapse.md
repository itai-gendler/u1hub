---
references:
  - kind: code
    role: implementation
    target: modules/timelapse.js#register
---

# Timelapse

A short video of one U1 print, one chamber-camera frame per layer, saved to the timelapse folder when the print finishes.

## Information kept

- **Printer name** — The printer it was filmed on.
- **File** — The file printed.
- **Started** — When the print started.
- **Frames** — Frames captured so far.
- **Video** — The saved video, named after the printer, the file and the time.

## States

### Recording

A frame is captured at each new layer.

### Saved

The video is in the timelapse folder.
