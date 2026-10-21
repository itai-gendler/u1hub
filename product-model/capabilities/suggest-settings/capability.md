---
availability:
  - place: hub::dashboard
domain: models
references:
  - kind: code
    role: implementation
    target: modules/advisor.js#modelBriefLines
  - kind: code
    role: implementation
    target: modules/advisor.js#parseSuggestion
  - kind: code
    role: implementation
    target: modules/mesh3mf.js#facts3mf
---

# Suggest settings

Suggest settings on a model card: Claude proposes the slicer settings for that model on a chosen printer before it is sliced, using the operator's own key and only when asked.
