---
kind: primary
routes:
  web: Web
steps:
  - text: A day has passed since the last check, with update checks on
    kind: condition
    unattended: true
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - Update checks
    contexts:
      web:
        place: hub::dashboard::hub-version
  - text: The Product fetches the release file and notes the newest version
    kind: product
    entities:
      - entity: hub-settings
        effect: changes
        facts:
          - Latest version
    contexts:
      web:
        place: hub::dashboard::hub-version
  - text: When it is newer than the running Hub, the version chip carries a notice with the release notes
    kind: product
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - Latest version
    contexts:
      web:
        place: hub::dashboard::hub-version
---

# The daily check finds a release

## Trigger

A Hub left running for weeks.

## Outcome

The operator learns a new release exists; Not now hides the notice for that version.
