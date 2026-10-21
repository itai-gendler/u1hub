---
singleton: true
domain: settings
references:
  - kind: code
    role: implementation
    target: modules/advisor.js#MODELS
---

# AI pre-flight settings

The operator's own Anthropic key and model choice for both AI buttons. Both buttons are off until a key is in.

## Information kept

- **Anthropic API key** — Kept on the Hub computer and never shown again; only its last four characters are shown.
- **Claude model** — Sonnet (recommended), Haiku (cheapest) or Opus (most thorough).
