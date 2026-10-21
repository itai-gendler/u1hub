---
entities:
  - entity: printer
    shows:
      - Name
      - Plate objects
references:
  - kind: code
    role: implementation
    target: public/app.js#refreshPlate
---

# Plate

One running print's plate seen from the front of the bed, the object printing now and the ones skipped, where an object is tapped to skip it.
