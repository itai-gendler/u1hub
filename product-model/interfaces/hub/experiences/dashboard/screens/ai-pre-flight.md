---
entities:
  - entity: ai-settings
    shows:
      - Anthropic API key
      - Claude model
    collects:
      - Anthropic API key
      - Claude model
references:
  - kind: code
    role: implementation
    target: public/modules/advisor-ui.js
---

# AI pre-flight

The Anthropic key, the model, and a link to read the exact brief for the selected file.
