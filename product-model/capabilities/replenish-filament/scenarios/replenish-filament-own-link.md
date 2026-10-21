---
kind: alternate
routes:
  web: Web
steps:
  - text: Presses Replenish on Amazon on a row whose spool has a buy link
    kind: actor
    actor: farm-operator
    entities:
      - entity: spool
        effect: reads
        facts:
          - Buy link
    contexts:
      web:
        place: hub::dashboard::resources
  - text: 'The Product opens the link: an Amazon product link carries the affiliate tag while affiliate links are on, and any other shop''s link is opened as it was typed'
    kind: product
    actor: farm-operator
    entities:
      - entity: hub-settings
        effect: reads
        facts:
          - Affiliate links
    contexts:
      web:
        place: hub::dashboard::resources
---

# Open the spool's own buy link

## Trigger

The operator buys this roll from one place.

## Outcome

The usual shop's page is open.
