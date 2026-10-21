---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses Remove key
    kind: actor
    actor: farm-operator
    entities:
      - entity: ai-settings
        effect: reads
        facts:
          - Anthropic API key
    contexts:
      web:
        place: hub::dashboard::ai-pre-flight
  - text: The Product forgets the key
    kind: product
    actor: farm-operator
    entities:
      - entity: ai-settings
        effect: changes
        facts:
          - Anthropic API key
    contexts:
      web:
        place: hub::dashboard::ai-pre-flight
---

# Remove the key

## Trigger

The AI buttons are no longer wanted.

## Outcome

Both buttons are off and nothing can be sent.
