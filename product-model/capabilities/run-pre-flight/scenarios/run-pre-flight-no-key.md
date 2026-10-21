---
kind: validation
routes:
  web: Web
steps:
  - text: Presses AI pre-flight
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dash
  - text: No Anthropic API key is saved
    kind: condition
    entities:
      - entity: ai-settings
        effect: reads
        facts:
          - Anthropic API key
    contexts:
      web:
        place: hub::dashboard::dash
  - text: The Product sends nothing and points to Settings, AI pre-flight
    kind: product
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::dash
---

# Pre-flight without a key

## Trigger

The button is tried before a key is set.

## Outcome

Nothing leaves the network.
