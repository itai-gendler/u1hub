---
appliesTo:
  - type: entity
    id: printer-type
    effect: removes
permits:
  - actors:
      - farm-operator
    when:
      - fact: Built-in
        is: 'No'
      - fact: Printers
        is: 0
references:
  - kind: code
    role: implementation
    target: core/library.js
---

# Only an added type with no printers is deleted

The built-in U1 type stays, and a type with printers waits until they are moved or removed. Its folder and files are never deleted.
