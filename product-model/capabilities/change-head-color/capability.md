---
availability:
  - place: hub::dashboard
domain: dash
references:
  - kind: code
    role: implementation
    target: core/filament.js#splitMaterial
  - kind: code
    role: implementation
    target: public/app.js#setColor
  - kind: code
    role: implementation
    target: public/app.js#colorPopHtml
---

# Change a head's color

Tapping a head's color on an idle printer to set what is loaded in it, color and material, the way the touchscreen would. It stays on the printer like a color set there.
