---
kind: primary
routes:
  web: Web
steps:
  - text: Pastes an Anthropic API key, picks Sonnet, Haiku or Opus and presses Save
    kind: actor
    actor: farm-operator
    entities:
      - entity: ai-settings
        effect: reads
        facts:
          - Claude model
    contexts:
      web:
        place: hub::dashboard::ai-pre-flight
  - text: The Product keeps the key on the Hub computer and shows only its last four characters from then on
    kind: product
    actor: farm-operator
    entities:
      - entity: ai-settings
        effect: changes
        facts:
          - Anthropic API key
          - Claude model
    contexts:
      web:
        place: hub::dashboard::ai-pre-flight
---

# Turn on the AI buttons

## Trigger

The operator made a key at Anthropic.

## Outcome

AI pre-flight on the Dash and Suggest settings on Models are live.

## Edge cases

- Show the brief for the selected file opens exactly what would be sent, before any key is trusted with it.
