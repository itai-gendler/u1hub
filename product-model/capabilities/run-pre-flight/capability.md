---
availability:
  - place: hub::dashboard
domain: dash
references:
  - kind: code
    role: implementation
    target: modules/advisor.js#briefFromText
  - kind: code
    role: implementation
    target: modules/advisor.js#printerBrief
  - kind: code
    role: implementation
    target: modules/advisor.js#parseVerdict
  - kind: code
    role: implementation
    target: public/modules/advisor-ui.js
---

# Run AI pre-flight

The ✦ AI pre-flight button on the selected file: Claude reads the settings baked into the sliced file against what is actually loaded in the chosen printer, using the operator's own Anthropic key, and only when pressed.
