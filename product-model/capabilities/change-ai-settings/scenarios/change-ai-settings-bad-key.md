---
kind: validation
routes:
  web: Web
steps:
  - text: Pastes text that does not start with sk-ant- and presses Save
    kind: actor
    actor: farm-operator
    entities: []
    contexts:
      web:
        place: hub::dashboard::ai-pre-flight
  - text: The Product refuses
    kind: product
    actor: farm-operator
    entities:
      - entity: ai-settings
        effect: reads
        facts:
          - Anthropic API key
    contexts:
      web:
        place: hub::dashboard::ai-pre-flight
---

# Refuse something that is not a key

## Trigger

The wrong value was pasted.

## Outcome

The saved key is unchanged.
