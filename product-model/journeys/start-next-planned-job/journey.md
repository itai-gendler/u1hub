---
actors:
  - farm-operator
references:
  - kind: code
    role: implementation
    target: public/modules/dispatch-ui.js
  - kind: code
    role: implementation
    target: public/app.js#pushTo
---

# Start the next planned job

## Goal

A printer whose bed was just cleared is printing the next copy Dispatch planned for it.

## Success criterion

The planned file is printing on that printer with its heads confirmed by the operator.
