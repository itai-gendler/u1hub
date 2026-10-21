---
availability:
  - place: hub::dashboard
domain: dash
references:
  - kind: code
    role: implementation
    target: modules/camera.js#register
  - kind: code
    role: implementation
    target: public/app.js#mountCameras
---

# Watch the chamber camera

Live view of a U1's chamber camera on its card, on demand so a phone on cellular is not streaming every printer.
