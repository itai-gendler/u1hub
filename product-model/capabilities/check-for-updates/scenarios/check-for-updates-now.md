---
kind: alternate
routes:
  web: Web
steps:
  - text: Opens the version chip and presses Check now
    kind: actor
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - Latest version
    contexts:
      web:
        place: hub::dashboard::hub-version
  - text: The Product fetches the release file and shows the installed and latest versions
    kind: product
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: changes
        facts:
          - Latest version
    contexts:
      web:
        place: hub::dashboard::hub-version
---

# Check now

## Trigger

The operator wonders whether they are current.

## Outcome

The panel says whether a newer release exists.
