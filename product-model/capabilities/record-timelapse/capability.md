---
availability:
  - place: hub::dashboard
references:
  - kind: code
    role: implementation
    target: modules/timelapse.js#register
  - kind: code
    role: implementation
    target: modules/timelapse.js#keepFrames
---

# Record a timelapse

Filming a U1 print from its chamber camera, one frame at each new layer, and saving the video when the print finishes. It never pauses or moves a print to get a frame.
