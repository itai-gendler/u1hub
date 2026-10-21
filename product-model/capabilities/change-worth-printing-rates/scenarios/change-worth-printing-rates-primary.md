---
kind: primary
routes:
  web: Web
steps:
  - text: Sets the sell floor and the filament cost per gram and saves
    kind: actor
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - Sell floor per gram
          - Filament cost per gram
    contexts:
      web:
        place: hub::dashboard::settings
  - text: The Product keeps the rates; a blank field goes back to the default
    kind: product
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: changes
        facts:
          - Sell floor per gram
          - Filament cost per gram
    contexts:
      web:
        place: hub::dashboard::settings
---

# Set the farm's own rule of thumb

## Trigger

This farm's numbers differ from the defaults.

## Outcome

Every file's line under the Dash uses the new rates.
